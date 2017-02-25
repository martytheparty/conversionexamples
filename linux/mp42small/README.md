ffmpeg -i ot_talent02.mp4 scale="trunc(oh*a/2)*2:720" -c:a copy ot_talent02_sm.mp4
ffmpeg -i input.avi -s 720x480 -c:a copy output.mkv


???????
