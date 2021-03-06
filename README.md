baidupan_shell
============

## 项目简介
百度盘管理终端  
**使用说明逐步移至wiki中**  
**MacOSX下测试通过，Windows下的编码问题基本解决**  

## 环境要求
已更新到wiki  

## 使用方式
已更新到wiki  

## 命令说明(逐步转移到wiki)
**命令参数中带空格的情况下，请将参数用双引号引起来**

#### login - 登录
格式：login your-account your-password  
登录后会保存cookie，下次使用时不用重新登录  
如需换号直接再执行login命令即可  
**登录时需要输入验证码的情况尚未处理**  
**考虑将登录功能加到启动参数中，去掉此指令**  

#### conf - 配置
格式：conf config-name config-value  
不带参数时，列出全部配置项；只传入config-name时，列出对应配置项的值；同时传入config-name和config-value时，表示更新配置  
目前有效的配置包括：
 * downloader: 要使用的下载器，可选aria2c/curl/wget，默认curl
 * localhome: 初始的本地工作目录

#### ls - 列印文件  
格式：ls file-type  
列印指定类型的文件  
file-type为可选参数，不传时列出全部文件  
要列出目录时，file-type传dir，其它情况传文件扩展名，如zip、mp4  
可同时传入多个file-type，以空格分开，如```ls dir zip rar```   

#### cd - 改变远程工作目录
格式：cd remote-dir  
remote-dir可输入相对路径或绝对路径  

#### lcd - 改变本地工作目录
格式：lcd local-dir  
remote-dir可是输入相对路径或绝对路径  
**lcd指令在Windows系统下有问题，待修复**

#### pwd - 输出工作目录
格式：pwd  
会显示远程工作目录和本地工作目录  

#### mkdir - 创建目录
格式：mkdir dir-name  
在远程当前目录下，创建指定名称的目录  
若已存在同名目录则不创建  

#### rm - 删除文件
格式：rm fileid1-to-delete fileid2-to-delete ...  
可批量删除网盘中的文件  
**只可删除用ls命令列出过的文件，因为列印出的文件会缓存起来**  

#### push - 上传
格式：push file1-to-upload file2-to-upload ...  
file-to-upload可以是绝对路径或相对路径  
使用相对路径时，是相对于本地工作目录  
文件将上传到远程工作目录下  
可一次上传多个文件  
依赖curl工具  

#### pull - 下载
格式：pull fileid1-to-download fileid2-to-download ...  
默认使用curl下载，支持wget和aria2c，通过conf指令配置  
**只可下载用ls命令列出过的文件，因为列印出的文件会缓存起来**  

#### play - 播放
格式：play fileid-to-play  
调用mplayer进行播放  
暂无其它需要支持的播放器  

#### tasks - 列出离线任务  
格式：tasks  
列出全部离线任务，包括正在进行的和已完成的  

#### dl - 离线下载  
已移至wiki  
该命令预计调整，合并tasks的功能  

#### exit - 退出  
格式：exit  
退出终端  

## 后续开发计划
 * 增加命令：mv（移动文件）、rename（重命名）、share（分享文件）等
 * 除baidupan_cli外，增加baidupan_push等直接执行特定动作的接口，便于和脚本结合
 * 其他：欢迎提供建议……