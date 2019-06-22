# asr-linux-cpp-change
## 本次修改仅限于asrDemo2
长语音识别，在百度sdk的基础上修改了一下，将pcm格式文件放入pcm中运行即可
[百度linux c++ sdk 文档](http://ai.baidu.com/docs/#/ASR-Linux-SDK/top)
[百度linux c++ sdk 下载](http://ai.baidu.com/sdk#asr)
## 自行修改部分
该demo自行修改的部分仅有三处
+ pcm文件
+ 文件的绝对路径，在asrDemo2/src/yours_main.cpp中，有个recog_one_file()函数，修改第一行的文件路径为自己的文件路径即可（查看方法：在当前路径下输入pwd命令）
+ yours_main.cpp中的AppID,APIkey,SecretKey修改为自己的
### 直接运行
sh build_and_run.sh
### 后台运行
nohup sh build_and_run.sh >output.out 2>&1 &
+ 查看后台
+ tail -f output.out

## 转pcm格式——ffmpeg
官方文档建议使用pcm格式转码
本人用的m4a转pcm，使用者自行修改
注意要符合文件格式
### 单独转
ffmpeg -i 1.m4a -f s16le -ar 16000 -ac 1 -acodec pcm_s16le 1.pcm
### 批量转
for i in *.m4a;do ffmpeg -y -i "$i" -acodec pcm_s16le  -f s16le  -ac 1 -ar 16000  "${i}.pcm";rename .m4a.pcm .pcm  *.m4a.pcm;done;find *.m4a|xargs rm -rf

=====
## 重要文件介绍
### 初始目录
基于./sample/asrDemo2/
### 识别文件放置文件夹
run/radio/
### 错误文件名&错误码
run/err_record.txt
### 音频文件放置位置
pcm/
