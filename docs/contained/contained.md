# containerd命令

## 登录容器
```bash
ctr tasks exec -t --exec-id abc ce38f1af906c /bin/bash
```

## 创建一个后台运行的容器实例，挂载目录使用--mount参数src表示宿主机目录dst表示容器内目录
```bash
ctr run -d --rm --env URL_SIZE=1 --net-host --mount type=bind,src=/root,dst=/root,options=rbind:ro --mount type=bind,src=/home,dst=/home,options=rbind:ro harbor.ld-hadoop.com/spider/test-env:1.5 <container_id> /bin/sh
```

## 停止任务
```bash
ctr tasks ls
ctr tasks kill -s SIGKILL <container_id>
ctr tasks rm <container_id>
```

## 进入容器，进行操作
```bash
ctr tasks exec -t --exec-id <your_temp_id> <container_id> /bin/sh
exit 退出
```

## pull镜像
```bash
ctr images pull harbor.ld-hadoop.com/spider/spiderprocessor-python2:releasev20211101.3
```
