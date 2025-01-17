# 162-linux-exectl-based-on-xattr
## 项目名称
linux基于文件扩展属性的执行控制

## 项目描述
随着linux系统的普及越来越广泛，针对linux系统的恶意攻击也越来越多，因此linux系统的安全性显得越发重要。对于从网上下载、U盘拷贝、本地新建等方式新建，及被篡改的可执行文件，默认不允许其执行，从而降低被恶意攻击的风险，来保证系统的安全性。

## 所属赛道
2022全国大学生操作系统比赛的“OS功能挑战”赛道

## 参赛要求
- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生/研究生
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2022全国大学生操作系统比赛”的章程和技术方案要求

## 项目导师
- 杨诏钧 yangzhaojun@kylinos.cn
- 姬一文 jiyiwen@kylinos.cn
- 王玉成 wangyucheng@kylinos.cn
- 杨钊 yangzhao@kylinos.cn

## 难度
高

## 特征
- 需要了解linux内核模块开发流程
- 需要了解LSM安全模块开发
- 需要了解文件系统内核相关知识
- 需要了解ftrace机制
- 需要了解linux系统二进制程序、脚本等执行过程

## 参考文档
- https://www.kernel.org
- https://www.kernel.org/doc/
- 《深入Linux内核架构（中文版）》

## License
GPL-3.0

## 预期目标
- 系统文件合法标识，设置扩展属性“security.kylin=verified”
- 系统文件非法标识，设置扩展属性“security.kylin=unknown”
- 被标识为非法标识的文件不允许执行，只有被标识为合法标识的文件才允许执行
#### 第一题：二进制程序执行控制
1. 实现对系统新文件创建进行监控，并自动给新文件设置非法标识
2. 实现LSM模块，对程序执行进行管控，不允许非法标识的程序执行
3. 合法标识文件移动后，在新路径下的文件，默认不允许执行
4. 合法文件，通过vim等命令打开，并保存退出后，若文件内容没发生改变，应该允许其执行

#### 第二题：脚本文件常规执行控制
以第一题为基础，实现对shell（bash、dash）、python、php、perl、java、awk等解释性语言编写的文件或程序的执行进行管控，管控方法覆盖的以上语言越多得分越高。如下的执行方式需要被管控：
```
# ./test.sh
# sh test.sh
```

#### 第三题：脚本管道或重定向执行控制
以第一题为基础，实现以下功能：
1. 实现对脚本管道执行控制，其执行方式如：
```
# cat test.sh | sh
```
2. 实现对脚本重定向执行控制，其执行方式如：
```
# sh < test.sh
```

