# Ansible自动化运维

```
列出命令模块ansible-doc   
[root@CentOS7 ~]#ansible-doc hostname -s
- name: Manage hostname
  hostname:
      name:                  # (required) Name of the host

[root@CentOS7 ~]#ansible-doc -s ping
- name: Try to connect to host, verify a usable python and return `pong' on success
  ping:
      data:                  # Data to return for the `ping' return value. If this parameter is
                               set to `crash', the module will
                               cause an exception.

列出管理主机列表，但不进行操作
ansible all --list-hosts
列出特定主机列表
ansible websrve --list-hosts  

aansible websrve -m ping   #基于ssh协议，需要加host-key验证，否则没有权限访问会失败
解决：
vim /etc/ansible/ansible.cfg
#host_key_checking = False        # 检查对应服务器host_key，建议取消#

ansible 192.168.37.27 -m ping -k   访问单个主机
ansible all -m pinig -k    访问全部管理主机，因为缓存上次验证密码，输入单个主机密码，也可全部访问全部管理主机

指定账号访问
ansible all -m ping -k -u wang

ansible <host-pattern> [-m module_name] [-a args]
--version 显示版本
-m module 指定模块，默认为command
-v 详细过程 –vv -vvv更详细
--list-hosts 显示主机列表，可简写 --list
-k, --ask-pass 提示输入ssh连接密码，默认Key验证
-C, --check 检查，并不执行
-T, --timeout=TIMEOUT 执行命令的超时时间，默认10s
-u, --user=REMOTE_USER 执行远程执行的用户
-b, --become 代替旧版的sudo 切换
--become-user=USERNAME 指定sudo的runas用户，默认为root
-K, --ask-become-pass 提示输入sudo时的口令


基于key验证,免密登录
192.168.37.7节点：
ssh-keygen
ssh-copy-id 192.168.37.6
ssh-copy-id 192.168.37.17
ssh-copy-id 192.168.37.27

ansible-galaxy install geerlinguy.ntp


![title](.local/static/2019/6/3/1563325040056.1563325040250.png)![title](https://i.loli.net/2019/07/17/5d2e727c7baa295222.png)

![image.png](0)
```

![title](.local/static/2019/6/3/1563325097828.1563325097829.png)

![title](https://i.loli.net/2019/07/17/5d2e72bfd746552777.png)


![title](.local/static/2019/6/3/1563325689435.1563325689545.png)

https://i.loli.net/2019/07/17/5d2e72bfd746552777.png
![15602420441.jpg](1)


![15602442471.jpg](0)







