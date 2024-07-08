# Windows 搭建远程服务器

## 背景

服务器状况：Win11 台式机、校园网有线连接、无公网 IP

服务器 IPV4 地址：10.66.123.123

服务器用户名：MyServer

服务器密码：12345

个人电脑用户名：MyLaptop

**核心思路：SSH+内网穿透实现外网访问**

## 服务器配置

### 永不休眠模式

设置 > 系统 > 电源和电池 > 设置“插入电源后，系统永不休眠“

### 使用 Powershell 代替 SSH 的默认终端 cmd(可选)

```powershell
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" `
   -Name DefaultShell `
   -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" `
   -PropertyType String `
   -Force
```

## SSH 服务器

### 安装

1. 设置 > 应用 > 可选功能 > 添加可选功能 > OpenSSH 服务器与客户端
2. 启动 SSH 服务`net start sshd` 或 `Start-Service sshd`
3. 设置 SSH 服务器开机自启`Set-Service -Name sshd -StartupType 'Automatic'`
4. 确认防火墙已开启对应端口(默认为 22)`Get-NetFirewallRule -Name *ssh*`

> 若防火墙规则不存在，则运行以下命令创建规则

```powershell
New-NetFirewallRule -Name sshd `
   -DisplayName 'OpenSSH Server (sshd)' `
   -Enabled True `
   -Direction Inbound `
   -Protocol TCP `
   -Action Allow `
   -LocalPort 22
```

### 密码登录

1. 个人电脑终端输入`ssh MyServer@10.66.123.123`
2. 输入密码`12345`，注意：输入密码的过程不会显示

### 免密登录(密钥)

**核心思路：将个人电脑中的公钥拷贝至服务器的 authorized_keys 文件中，从而实现非对称加密**

1. 编辑服务器文件 C:/ProgramData/ssh/sshd_config

   ```
   # 开启公钥登录和设置认证文件
   PubkeyAuthentication yes
   AuthorizedKeysFile .ssh/authorized_keys

   # 取消默认认证文件
   # Match Group administrators
   # AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
   ```

2. 修改完毕后，重启 SSH 服务`Restart-Service sshd`

3. 在个人电脑生成密钥`ssh-keygen`, 完成操作后 C:/Users/MyLaptop/.ssh/目录下会出现 id_rsa 系列文件

4. 将个人公钥 id_rsa.pub 文件中的内容拷贝至服务器的 authorized_keys 文件中

   > 个人公钥位置：C:/Users/MyLaptop/.ssh/id_rsa.pub
   >
   > 服务器的 authorized_keys 位置：C:/Users/MyServer/.ssh/authorized_keys

5. 配置服务器 authorized_keys 文件的权限。文件名右键 > 安全 > 高级；禁用继承，只保留 Administrator 和 System 的权限条目，其余权限删除

6. 个人电脑终端输入`ssh MyServer@10.66.123.123`即可免密登录

### 相关命令

```shell
# 查看ip地址
ipconfig

# 查看GPU状态
nvidia-smi

# 查看状态
Get-Service sshd

# 启动SSH Server 二选一
net start sshd
Start-Service sshd

# 停止SSH Server 二选一
net stop sshd
Stop-Service sshd

# 重启SSH Server 二选一
net stop sshd; net start sshd;
Restart-Service sshd

# 安装SSH Server
sudo apt install openssh-server

# 查看SSH服务是否开启
ps aux|grep ssh

# 开启服务
sudo systemctl start ssh.service

# 本地生成公钥
ssh-keygen -R "远程服务器ip地址"
```

## 内网穿透

仅配置 SSH 只能保证在局域网(LAN)中使用，要想在外网访问，需配置内网穿透。

推荐使用软件配置：花生壳 https://hsk.oray.com/

内网穿透完毕后，使用如下命令进行 SSH 登录

假设端口号 123 域名 abc.de.f

```shell
ssh -p 端口号 MyServer@域名
ssh -p 123 MyServer@abc.de.f
```

## 管理软件推荐

WinSCP：https://winscp.net/eng/index.php

Termius：https://www.termius.com/

Tabby：https://github.com/eugeny/tabby
