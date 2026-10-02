Assets in this folder
----------------------
All assets below are real, locally generated files (no external URLs are
used anywhere on the site). Generated with Python/Pillow and ffmpeg
(installed via Homebrew).

Images (Python / Pillow)
-------------------------
logo.svg          - Site logo (hand-written vector), used in the <header>
                     of every page.
icon-*.svg        - Nine small two-color icon cards (64x64, hand-written
                     vector) for the "What You Will Find" cards on
                     index.html: icon-home, icon-text, icon-links,
                     icon-lists, icon-tables, icon-forms, icon-media,
                     icon-semantic, icon-metadata.
hero.jpg          - 1200x480 gradient + geometric hero banner with the
                     "HTML Review" headline, used as the index.html hero
                     background.
sample.jpg        - 800x500 gradient/pattern placeholder "photo", used for
                     <img>, <figure>, <embed>/<object> examples.
sample-small.jpg  - 400px-wide version of the same artwork, used as the
                     <picture> fallback <img>.
sample-large.jpg  - 1200px-wide version of the same artwork, used as the
                     wide-viewport <source> candidate inside <picture>.

Video (ffmpeg)
--------------
intro.mp4   - 640x360, ~7s, H.264/yuv420p, silent. Built from an animated
              two-color gradient (lavfi "gradients" filter) with rotating
              geometric shapes and a text overlay ("HTML Review"),
              composited with ffmpeg filters. ~130 KB.
intro.webm  - Same clip encoded as VP9/WebM, offered as the first
              <source> candidate before the MP4 fallback. ~55 KB.
poster.jpg  - A single frame extracted from intro.mp4 with
              `ffmpeg -ss 2 -frames:v 1`, used as the <video poster="...">
              image so the player never shows a blank black rectangle.

Audio (ffmpeg)
--------------
tone.mp3 / tone.wav - A 2.5-second C major chord (three sine waves at
              523.25 Hz / 659.25 Hz / 784.00 Hz mixed with ffmpeg's `amix`,
              faded in/out) instead of a single harsh beep. Shipped in two
              formats so the <audio><source> example demonstrates a real
              format fallback (MP3 first, WAV second).

Regeneration
------------
These commands (run from the project root) reproduce the ffmpeg-based
assets if they ever need to change:

  ffmpeg -f lavfi -i "gradients=s=640x360:d=7:r=25:c0=0x1a4e85:c1=0x2b6cb0:speed=0.08" \
         -i <rotating-shapes.png> -i <text-overlay.png> \
         -filter_complex "..." -t 7 -c:v libx264 -crf 24 -pix_fmt yuv420p images/intro.mp4

  ffmpeg -i images/intro.mp4 -ss 2 -frames:v 1 images/poster.jpg

  ffmpeg -f lavfi -i "sine=frequency=523.25:duration=2.5" \
         -f lavfi -i "sine=frequency=659.25:duration=2.5" \
         -f lavfi -i "sine=frequency=784.00:duration=2.5" \
         -filter_complex "amix=inputs=3,afade=t=in:d=0.3,afade=t=out:st=2:d=0.5" \
         -c:a libmp3lame images/tone.mp3
