# GPU limit management

机器学习领域的一些实验，由于参数较多，通常需要对不同参数跑多组实验。

本项目维护使用GPU程序的任务队列，动态调度任务。避免手动跑实验带来的繁琐感受。

## install

代码还在大改中，bug仍很多。。。

### 源码安装

```bash
git clone https://github.com/lichunown/gpu-limit.git
cd gpu-limit
python setup.py install
```
### pip 安装

```bash
pip3 install gpulimit
```

## usage

本程序使用linux socket进行交互，后台`gpulimit_server`动态调度，前台`gpulimit`发送命令，获取信息。

### 启动后台服务

```bash
gpulimit_server # 直接启动
nohup gpulimit_server & # 后台运行
```

### 前台命令

```bash
$ gpulimitc help

GPU Task Manage:
    usage:

        client.py -h                  show help
        gpulimit add [cmds]           add task [cmds] to gpulimit queue.


    other commands:

        help [cmd]                    show help
        add [cmds]                    ls GPU task queue status
        ls                            ls GPU task queue status
        show [id]                     show task [id] details.
        rm [id]                       remove task [id] from manage, 
        							  	if task is running, kill it.
        							  
        kill [id]                     kill task [id]
        move [id] [index(default=0)]  move [id] to [index]
        set [name] [value]            set some property.
        start [id defalut=None]       Force start task(s).
        log [id]                      show [id] output.
        status                        show System status.
        debug [id]                    if task [id] is `CMD_ERROR`, 
                                      	use this show error traceback.
```

#### 添加任务

```bash
gpulimit add [cmds]
# for example
# gpulimit add python3 main.py --lambda=12 --alpha=1
```

#### 查看任务

```bash
gpulimit ls
```

#### 查看任务信息

```bash
gpulimit ls
```

#### 查看任务输出日志

```bash
gpulimit log [task id]
```

同样，也支持查看`gpulimit_server`的后台输出：

```bash
gpulimit log main
```

## TODO list


- [x] change raise type, and add `try except` for exception break.
- [x]  \_\_doc\_\_
- [ ] kill all, range
- [ ] add commits
- [ ] use priority queue as task_manage.queue
- [ ] Improve scheduling aligorithm
- [ ] 

zhanxianyuan@jd.com

zhang.junbo@jd.com

zhangyue81@jd.com

zhuxiangyu5@jd.com

li.ming@jd.com

yinhonglei@jd.com

xuhaoran8@jd.com