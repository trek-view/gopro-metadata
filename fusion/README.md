# GoPro Fusion Overview

* Manufacturer: GoPro
* Model: Fusion
* On Sale: 2017 - 2020

## Overview of Fusion workflow

All videos and images on the Fusion are captured as 360's (both front and back lens).

Image captured are fish-eye and are saved on camera as .jpgs and video captures saved as .mp4s.

In either case, GoPro Fusion Studio must be used to stitch raw front and back photos. In Fusion Studio you can select either 360 output or overcapture (which is flat photo -- equivalent of HERO mode on other cameras).

## A note on GPS data in unstitched content

On all raw photo files (before stitched by GoPro Fusion studio) the GPS content for the frame can be found in the front image.

For all raw video files the front file contains the GPMF telemetry (GPS) track (track4) and the back file contains the camera metadata (track4).

## File Naming Conventions

### Unstitched Videos (360)

Every 360 video recorded creates 2 mp4 files (one from the front camera, the other from the back camera).

You can identify the front and the back recordings by the filenames.

* GP**BK**7152.MP4 (back)
* GP**FR**7152.MP4 (front)

The video filename is split into 3 identifying parts (I'll use `GPBK7152.MP4` as an example):

1. `GP`: always the same. Can be used as a simplistic way to identify a 360 video taken on the Fusion
2. `BK`: (second 2 letters): either BK (back camera) or FR (front camera)
3. `7152`: increases by one with each new video shot (i.e. user stops one video and starts the next). e.g. `GPBK7152.MP4` and `GPBK7153.MP4` are two distinct videos. In the case where a video is split into chapters ([see Chaptering](gopro-fusion-camera-modes.md#gopro-video-chaptering)), then the first digit is increased: `GPBK7153.MP4, GPBK8153.MP4, ...`

### Stitched Videos (equirectangular + overcapture)

Once the two 360 unstitched front/back mp4 files have been stitched by GoPro Fusion Studio a single mp4 is produced.

The output filename is derived from input where, GP**BK**7152.MP4 + GP**FR**7152.MP4 = VIDEO\_7152.mp4.

The video filename is split into 2 identifying parts:

1. `VIDEO_`: same for all stitched video files outputted by Fusion studio software
2. `7152:` the number inherited from the two mp4 files on input. Fusion Studio will only stitch files with matching filename

### Unstitched Single Photos (360)

Every 360 image captured created 2 jpg files (one from the front camera, the other from the back camera).

You can identify the front and the back recordings by the filenames.

* GPBK0004.JPG
* GPFR0004.JPG

The image filename is split into 3 identifying parts (I'll use `GPBK0004.JPG` as an example):

* `GP`: Always GP. Easy way to identify 360 single photo shot on the Fusion.
* `BK`: either BK (back camera) or FR (front camera). Easy way to identify 360 photo shot on the Fusion.
* 0004: increases by one with each photo shot.

### Stitched Photo (equirectangular + overcapture)

Once the two 360 unstitched front/back jpg files have been stitched by GoPro Fusion Studio a single jpg is produced

The output filename is derived from input where, GP**BK**0004.jpg + GP**FR**0004.jpg = PHOTO\_0004.jpg.

The video filename is split into 2 identifying parts:

1. `PHOTO_`: same for all stitched single photo files outputted by Fusion studio software
2. `0004:` the number inherited from the two jpg files on input. Fusion Studio will only stitch files with matching filenames.

### Unstitched Timelapse Photos (360)

Every 360 image captured created 2 jpg files (one from the front camera, the other from the back camera).

You can identify the front and the back recordings by the filenames.

* GB075169.JPG (back)
* GF075169.JPG (front)

The image filename is split into 3 identifying parts (I'll use `GF075169.JPG` as an example):

* `GB`: either BK (back camera) or FR (front camera). Easy way to identify 360 photo shot on the Fusion.
* `07:` (first 2 digits) increases by one with each new timelapse shot.
* `7152`: increases by one with each photo in the timelapse.

### Unstitched Timelapse Videos (360)

2 mp4 files (one from the front camera, the other from the back camera) are created.

These are named in the same way as non-timelapse videos.

### Stitched time lapse as images (equirectangular + overcapture)

Once the two 360 unstitched front/back files have been stitched by GoPro Fusion Studio a single jpg is produced for each frame in the timelapse. Only available if timelapse mode outputs .jpg.

The output filename is derived from input where, `GF075169.JPG` + `GFB75169.JPG` = MULTISHOT\_5169\_000000.jpg (assuming `GF075169.JPG` is the only photo (single photo mode), or first photo (in timelapse).

The image filename is split into 3 identifying parts (I'll use `GF075169.JPG` as an example):

* `MULTISHOT_`: Always the same. Easy way to identify timelapse 360 photo shot on the Fusion.
* `5169`_:_ first photo in ascending order in timelapse series. e.g. GF075169.JPG, GF075170.JPG, GF075171.JPG. If first photo was GF070012.JPG then would be MULTISHOT\_0012\_xxx.jpg
* `000000`: order of photo in timelapse. Starts at 000000 and increments by 1 for each photo in timelapse: MULTISHOT\_5169\_000000.jpg, MULTISHOT\_5169\_000001.jpg, ...

### Stitched time lapse as video (equirectangular + overcapture)

Once the two 360 unstitched front/back files have been stitched by GoPro Fusion Studio a single mp4 is produced. Available if timelapse mode outputs .jpg OR .mp4

These are named in the same way as non-timelapse videos.

## Video notes

### Video: Notes on upscaling

Note 1: it appears both 5.2k are both upscaled from raw mp4 files. Seems like 5.2k is actually 4k raw.

![](https://raw.githubusercontent.com/trek-view/gopro-metadata/notes/images/fusion-upscale.png)

### Video: thm, lrv and wav files

These files are not used by the app, but noted here for reference. These files are created whenever video files are shot on the camera (in any format):

* `.thm` files are JPG thumbnails (THM) used by GoPro software as a still photo preview of the video. They’re tiny files (usually less than 100Kb), typically with a resolution of 160 by 120 pixels.
* `.lrv` files are Low-Resolution Video (LRV) files are used by GoPro software to display video previews, without having to load the high-resolution version.
* `.wav` files are the audio recording of the video.

### Video: GoPro Video Chaptering

Here are the chapter lengths reported by GoPro for the Fusion camera ([https://community.gopro.com/t5/en/GoPro-Camera-File-Chaptering-Information/ta-p/390210](https://community.gopro.com/t5/en/GoPro-Camera-File-Chaptering-Information/ta-p/390210)):

> **HERO10 Black, HERO9 Black, HERO8 Black, MAX, HERO7 Black, HERO6 Black, Fusion, HERO5 Black & HERO5 Session, HERO4 Black & Silver, HERO (2018)**
>
> * Chapter size: approx. 4.0 GB (Samples of HERO9 Black recording times are below)
>   * 5k/30fps High Bitrate is approximately 5 minutes
>   * 1080p/60fps High Bitrate is approximately 7.5 minutes

During stitching, these video chapters can be stitched into one video. For example, GPFR0057.MP4 (7 min), GPBK0057.MP4 (7 min), GPFR0058.MP4 (7 min), GPBK0058.MP4 (7 min), GPFR0058.MP4 (26 sec), GPBK0058.MP4 (26 sec) would stitch into a single video VIDEO\_0057.mp4 (14 mins 26 sec).

GoPro Fusion raw (unstitched) videos on camera are limited to roughly 2.5gb (that's 2.5gb per video front and back -- so 5gb total for front+back). 2.5gb recordings will come when recording at 5.2k which is about 7 mins of footage. Stitched at 4k H264, the resultant video (full equirectangular) is much smaller at around 400mb.

When in 3k mode, each unsititched video is a maximum of 2.4gb which again equates to about 7 mins of footage.

Given the way multiple chaptered videos are stitched into one, it means stitched videos can theoretically be of any length. Although as a reference, to process 20 mins of video takes several hours in Fusion Studio on a well specced machine.

## Timelapse

### Timelapse photo: Notes videos

You can define the photo interval setting when shooting a timelapse video (e.g 0.5 seconds, 1 second, 2 second...)

When the video is stitched, the framerate of the timelapse is always 29.97 (30) FPS, wether shooting at 3K or 5.2 (you can see this in stitched metadata of video under the `Track1:VideoFrameRate` tag)

As an example, if shooting at 0.5 second setting, you will need at least 15 seconds of footage for 1 second of video (30 fps output / 0.5 fps captured).