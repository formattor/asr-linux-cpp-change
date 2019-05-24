# asr-linux-cpp-change
## 只修改了asrDemo2
长语音识别，在百度sdk的基础上修改了一下，将pcm格式文件放入pcm中运行即可
### 直接运行
sh build_and_run.sh
### 后台运行
nohup sh build_and_run.sh >output.out 2>&1 &
+ 查看后台
- tail -f output.out

## 转pcm格式——ffmpeg
本人用的m4a转pcm，使用者自行修改
注意要符合文件格式
### 单独转
ffmpeg -i 1.m4a -f s16le -ar 16000 -ac 1 -acodec pcm_s16le 1.pcm
### 批量转
for i in *.m4a;do ffmpeg -y -i "$i" -acodec pcm_s16le  -f s16le  -ac 1 -ar 16000  "${i}.pcm";rename .m4a.pcm .pcm  *.m4a.pcm;done;find *.m4a|xargs rm -rf 