Split video
* ffmpeg -ss 00:00:30 -t 10 -i input.mov output_part4.mov

Split video by chapter
* mkvmerge -o output.mkv --split chapters:all input.mkv
* Ref: https://superuser.com/questions/795373/split-mkv-based-on-chapters/892418#892418