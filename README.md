# ffmpeg-doc

FFMPG EXAMPLES
--------------

ffmpeg [global_options] {[input_file_options] -i input_url} ... {[output_file_options] output_url} ...

FILTER EXAMPLE: 
--------------
-vf fillborders = arg1=1 : arg2=2 : arg3=3

FRAMERATE OUTPUT:
-----------------
ffmpeg -i input.mp4 -r 24 out.mp4

BITRATE:
--------
ffmpeg -i input.mp4 -b:v 64k -bufsize 64k out.mp4

JOIN:
-----
ffmpeg -i input.mp4 -i 2.mp4 -i 3.mp4 out.mp4

TRIM:
-----
[-][HH:]MM:SS[.m...]

ffmpeg -ss 00:00:00 -i input.mp4 -c copy -t 00:00:05 output.mp4

CROSSFADE:
---------
ffmpeg -i input.mp4 -i 2.mp4 -filter_complex xfade=transition=fade:duration=2:offset=5 output.mp4
 
HORIZONTAL BORDERS:
--------
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
