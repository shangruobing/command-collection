# Windows搭建远程服务器

## 背景

服务器状况：Win11台式机、校园网有线连接、无公网IP

服务器IPV4地址：10.66.123.123

服务器用户名：MyServer

服务器密码：12345

个人电脑用户名：MyLaptop

**核心思路：SSH+内网穿透实现外网访问**



## 服务器配置

### 永不休眠模式

设置 > 系统 > 电源和电池 > 设置“插入电源后，系统永不休眠“

### 使用Powershell代替SSH的默认终端cmd(可选)

```shell
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```



## SSH服务器

### 安装

1. 设置 > 应用 > 可选功能 > 添加可选功能 > OpenSSH服务器与客户端
2. 启动SSH服务`net start sshd` 或 `Start-Service sshd`
3. 设置SSH服务器开机自启`Set-Service -Name sshd -StartupType 'Automatic'`
4. 确认防火墙已开启对应端口(默认为22)`Get-NetFirewallRule -Name *ssh*`

> 若防火墙规则不存在，则运行以下命令创建规则

```shell
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

### 密码登录

1. 个人电脑终端输入`ssh MyServer@10.66.123.123`
2. 输入密码`12345`，注意：输入密码的过程不会显示



### 免密登录(密钥)

**核心思路：将个人电脑中的公钥拷贝至服务器的authorized_keys文件中，从而实现非对称加密**

1. 编辑服务器文件 C:/ProgramData/ssh/sshd_config 
   ```
   # 开启公钥登录和设置认证文件
   PubkeyAuthentication yes
   AuthorizedKeysFile .ssh/authorized_keys
   
   # 取消默认认证文件
   # Match Group administrators
   # AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
   ```

2. 修改完毕后，重启SSH服务`Restart-Service sshd`

3. 在个人电脑生成密钥`ssh-keygen`, 完成操作后C:/Users/MyLaptop/.ssh/目录下会出现id_rsa系列文件

4. 将个人公钥id_rsa.pub文件中的内容拷贝至服务器的authorized_keys文件中

   >个人公钥位置：C:/Users/MyLaptop/.ssh/id_rsa.pub
   >
   >服务器的authorized_keys位置：C:/Users/MyServer/.ssh/authorized_keys

5. 配置服务器authorized_keys文件的权限。文件名右键 > 安全 > 高级；禁用继承，只保留Administrator和System的权限条目，其余权限删除

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
```



## 内网穿透

仅配置SSH只能保证在局域网(LAN)中使用，要想在外网访问，需配置内网穿透。

推荐使用软件配置：花生壳 https://hsk.oray.com/

内网穿透完毕后，使用如下命令进行SSH登录

假设端口号123 域名abc.de.f

```shell
ssh -p 端口号 MyServer@域名
ssh -p 123 MyServer@abc.de.f
```



## 管理软件推荐

WinSCP：https://winscp.net/eng/index.php

Termius：https://www.termius.com/

Tabby：https://github.com/eugeny/tabby

