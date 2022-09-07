# ansible安装


### 安装命令
```bash
apt-get install ansible
```

### 任一位置添加ip
```bash
vim /etc/ansible/hosts
172.16.100.[1:300]
172.16.103.[1:300]
172.16.183.[1:300]
```

### ansible_playbook配置，比如批量安装，python2_install.yaml
```bash
---
- hosts: python3_new
  user: root
  gather_facts: false
  tasks: 
  - name: 将Python拷到各个机子上
    copy: src=/root/Python-2.7.12.tgz dest=/root
  - name: 解压
    shell: tar xvf Python-2.7.12.tgz
  - name: 配置
    shell: ./configure --prefix=/usr/local/python2
  - name: 编译
    shell: make
  - name: 安装
    shell: make install
```

### ansible_playbook执行
```bash
ansible-playbook python2_install.yaml
```

### 批量创建crontab
```bash
ansible all -m cron -a " name='logrorate' minute=*/1 job='/usr/sbin/logrotate /etc/logrotate.d/spider' "
```
