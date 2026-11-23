# Infinara AR postcards

## Files
- index.html: the AR page (don't need to edit)
- config.json: one entry per postcard design, in the same order you uploaded them to the MindAR compiler
- targets/targets.mind: compiled image targets (you create this)
- videos/01.mp4, 02.mp4 ...: one video per design

## config.json
- "aspect" = card height / card width. Use the PHOTO area, not the full card. Last year file: photo 141.2 x 98.6 mm = 0.698. Video should be about 1.433:1 (e.g. 1720x1200).
- Order of "targets" must match the order of images in the .mind file.

## Steps
1. Compile targets: https://hiukim.github.io/mind-ar-js-doc/tools/compile
   Upload the postcard FRONT images (the exact print files, same crop as the printed card). Order = target index. Download targets.mind into /targets.
2. Export videos: MP4, H.264, AAC, 10-15 sec, under 10 MB each, same aspect ratio as the card. Put in /videos and match names in config.json.
3. Test locally on phone: needs HTTPS for camera. Easiest is to deploy first (step 4).
4. Deploy free: push this folder to a GitHub repo, Settings > Pages > Deploy from branch (main, root). URL will be https://<username>.github.io/<repo>/
5. Make a QR code of that URL (any free generator, set to high error correction) and print it on the back.

## Test before printing
Print one card at final size and paper, and scan it indoors and outdoors. Matte paper tracks better than gloss.

## Floating look (config.json)
"float": { "width": 0.87, "lift": 0.07, "bob": 0.012, "shadow": true }
- width: video width as a fraction of the photo width. 0.87 fits the video inside the photo (strips of photo show at the sides). 0.92 reaches the card border. Above ~0.96 it hangs past the card.
- lift: how high it floats above the card (0 = flat on the card).
- bob: how much it gently moves up and down (0 = still).
- shadow: soft shadow on the card under the video.
"videoAspect" = video height / width (1120x896 = 0.8). Set per video.
