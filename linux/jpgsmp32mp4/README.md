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
