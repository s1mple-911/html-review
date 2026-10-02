Assets in this folder
----------------------

logo.svg   - Site logo (vector), used in the <header> of every page.
sample.png - Small raster image generated with Python/Pillow, used for
             <img>, <picture> and <figure> examples.
tone.wav   - 2-second 440 Hz sine tone generated with Python's built-in
             `wave` module, used for the <audio> example.

sample.mp4 (video)
-------------------
`ffmpeg` was not available on the machine used to build this project, so no
local sample.mp4 could be rendered with:

  ffmpeg -f lavfi -i color=c=steelblue:s=320x240:d=3 -pix_fmt yuv420p images/sample.mp4

Because no local file exists, the <video> elements on links.html and
media.html point their <source> at a public sample video URL instead (so the
page never links to a missing local file). If ffmpeg becomes available,
run the command above, save the result as images/sample.mp4, and update the
<source src="..."> on those two pages to point at "images/sample.mp4" for a
fully offline demo.
