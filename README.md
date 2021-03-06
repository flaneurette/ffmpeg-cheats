# ffmpeg-cheats

ffmpeg is an excellent software, and can be used to manually create films without a distracting GUI or expensive software. Perhaps, in these days of 'rush', we are so used to GUI's that we rarely get to focus on the true creative process. By using ffmpeg, one has to be rather thoughtful and have much more patience and attention. Timing certain shots and carefully applying effects is a creative process in itself, which might turn out to be much more fun. Plus, I am able to learn ffmpeg, by actually using it on code level and need not to rely on anything else. Art is indeed long... it is a personal journey, not a quick destination and certainly not a 'product'. Products usually turn into products, and indeed, we cannot confuse the tools with the result, but temptation remains.

FFMPG EXAMPLES
--------------

	ffmpeg [global_options] {[input_file_options] -i input_url} ... {[output_file_options] output_url} ...

RAW VIDEO
---------
Convert a compressed mp4 into a raw avi container, in order to apply effects without much loss.

	ffmpeg -i input.mp4 -c:v rawvideo output.avi

STILLS
------
Slice film into PNG stills.

	ffmpeg -i input.mp4 -vcodec png -s 1920x1280 "C:\stills\%03d.png"
	
CONVERT STILL IMAGE & MP3 TO A MOVIE
------------------------------
	ffmpeg -loop 1 -framerate 2 -i image1920x1080.png -i music.mp3 -c:v libx264 -preset medium -tune stillimage -crf 18 -c:a copy -pix_fmt yuv420p -t 00:00:00 output.mkv

REPLACE AUDIO 
-------------

	ffmpeg -i input.mp4 -i audio.wav -map 0:v -map 1:a -c:a:v copy output.mkv

AVI TO MP4
----------
Convert AVI to compressed MP4.

	ffmpeg -i input.avi -c:v libx264 output.mp4

FRAMERATE OUTPUT:
-----------------
	ffmpeg -i input.mp4 -r 24 out.mp4

BITRATE:
--------
	ffmpeg -i input.mp4 -b:v 64k -bufsize 64k out.mp4

JOIN:
-----
Join 3 clips into a single output clip. First mux the .mp4's to .ts and then concat the files into a mp4:

	f.exe -i "concat:cut.ts|cut_2.ts|cut_3.ts" -c copy cut.mp4

TRIM & SLICE:
-----
Trim or 'slice' a 5 second clip from a 7 second input file. Time format: HH:MM:SS

	ffmpeg -i input.mp4 -ss 2 -to 7 -c copy cut.mkv
or:
	
	ffmpeg -i input.mp4 -ss 00:00:02 -to 00:00:07 cut.mp4

CROSSFADE:
--------- 
Cross fade two clips into a single clip.

	ffmpeg -i 1.mp4 -i 2.mp4 -filter_complex xfade=transition=fade:duration=2:offset=5 output.mp4
 
HORIZONTAL BORDERS:
-------------------
Create a letterbox, or 'horizontal blinds' over a video with a 100px height.

	ffmpeg -i input.mp4 -vf fillborders=left=1:right=1:top=100:bottom=100:mode=fixed output.mp4

SATURATION:
-----------
	ffmpeg -i input.mp4 -vf colorcorrect=saturation=3.0 output.mp4

COLORIZE:
---------
	ffmpeg -i input.mp4 -vf colorize=hue=300:saturation=1 output.mp4

NOISE:
------
	ffmpeg -i input.mp4 -vf noise=alls=80:allf=t+u output.mp4

CURVES:
---------
ffmpeg also provides a few 'presets' that can be applied through it's curves library.

	ffmpeg -i input.mp4 -vf curves=vintage output.mp4

	options:
	none
	color_negative
	cross_process
	darker
	increase_contrast
	lighter
	linear_contrast
	medium_contrast
	negative
	strong_contrast
	vintage

FILTER EXAMPLE: 
--------------
It is useful to know that ffmpeg, seemingly, delimits filter arguments/values with a ':'. 

Example:

	-vf colorize = arg1=1:arg2=2:arg3=3

USEFUL FILTERS:
--------------
https://ffmpeg.org/ffmpeg-filters.html

    anullsrc, (empty audio)
    boxblur, 
    chromahold,
    chromakey,
    chromashift,
    colorbalance,
    colorcontrast,
    colorcorrect,
    colorize,
    colorkey,
    colortemperature,
    convolution,
    crop, (input video)
    cover_rect,
    deflicker,
    deshake,
    drawbox,
    drawtext
    fade,
    fps, (force frame rate)
    fillborders,
    floodfill,
    gblur, (gaussian),
    hue,
    elbg (posterize),
    erosion,
    mandelbrot,
    maskfun, (create mask)
    monochrome,
    noise,
    normalize, (RGB),
    pseudocolor,
    sidechaincompress,
    stereowiden,
    shear,
    select, (select video frames to pass in the output)
    smartblur,
    tile,
    trim,
    vignette, 
    vibrance, 
    zoompan.

ENCODE
-----
Encode videos for videosharing platforms.
https://trac.ffmpeg.org/wiki/Encode/YouTube

WEBCAM
------
Record from webcam.
https://trac.ffmpeg.org/wiki/Capture/Webcam

STREAM
------
Capture and stream.
https://trac.ffmpeg.org/wiki/StreamingGuide

CAPTURE DESKTOP AUDIO & VIDEO
-----------------------------
Credit: https://www.codeproject.com/Tips/5291304/Video-Screen-Capture-with-Audio

	C:\ffmpeg.exe -f dshow -i audio="Stereo Mix (Realtek(R) Audio)" -f gdigrab -itsoffset 00:00:0.6 -i desktop -c:v libx264rgb -framerate 24 -crf 20 -preset ultrafast output-file.mp4



