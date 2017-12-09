0) Collect a bunch of jpgs into a folder

1) Resize all pictures to 10%
mogrify -resize 10% *.jpg

2) Convert all pictures to PNGs
mogrify -format png *.jpg  

3) Change them all into a movie
ffmpeg -framerate 1/3 -i '%d.png' -c:v libx264 -r 30 -pix_fmt yuv420p -vf 'scale=trunc(iw/2)*2:trunc(ih/2)*2' source.mp4

or

ffmpeg -pattern_type glob -framerate 1/3 -i '*.png' -c:v libx264 -r 30 -pix_fmt yuv420p -vf 'scale=trunc(iw/2)*2:trunc(ih/2)*2' source.mp4

or

ffmpeg -pattern_type glob -framerate 2.2 -i '*.png' -c:v libx264 -r 30 -pix_fmt yuv420p -vf 'scale=trunc(iw/2)*2:trunc(ih/2)*2' source.mp4


4) Add Music
ffmpeg -i source.mp4 -i source.mp3 -codec copy -shortest output.mp4

or FOR THE LONGEST INSTEAD OF CUTTING OFF AT THE END

ffmpeg -i source.mp4 -i source.mp3 -codec copy output.mp4

########################################
Alternative

1) Resize directory full of photos to a width of 600px
command:
convert '*.JPG[600x]' resized/resized%03d.jpg

2) Make all of the photos into an MP4
(1 second per shot: 3 => 3 frames per second: 1/3 => 1 frame every 3 seconds)
command:
ffmpeg -framerate 1 -i resized%03d.jpg -c:v libx264 -profile:v high -crf 20 -pix_fmt yuv420p output.mp4

3) Add Music
command:
ffmpeg -i output.mp4 -i audio.mp3 -codec copy -shortest final.mp4
