# GoPro MAX Overview

* Manufacturer: GoPro
* Model: MAX
* On Sale: 2021 - Present

## Overview of HERO10 workflow

Unlike 360 cameras, all final photos/vides are processed on the camera and can simply be downloaded from the SD card.

## File Naming Conventions

### Video: Hero Mode (.mp4)

The video filename is split into 3 identifying parts (I'll use `GX010048.MP4` as an example):

1. `GX`: always the same. Can be used as a simplistic way to identify a video in video mode taken on the HERO10.
2. `10`: (first 2 digits) the camera breaks videos longer than a certain size/length into separate files (see chaptering). Increases by one with each chapter recorded. For example, a 9 minute video would be split into 3 files (`GX010048.MP4`, `GX020048.MP4`, `GX030048.MP4)`.
3. `0048` increases by one with each new video shot (i.e. user stops one video and starts the next). e.g. `GX010048.MP4` and `GSGX010049.MP4` are two distinct videos.

### Single Photo / Nightmode

The image filename is split into 2 identifying parts (I'll use `GOPR0056.JPG` as an example):

* `GOPR` : always the same. Can be used as a simplistic way to identify a HERO photo taken on the HERO10 in single photo mode
* `8586:` count of the photo (increments by 1 each time between 0000 - 9999)

### &#x20;Single Photo Liveburst

The video filename is split into 3 identifying parts (I'll use `GG010059.MP4` as an example):

1. `GG`: always the same. Can be used as a simplistic way to identify a video in photo liveburst photo mode taken on the HERO10.
2. `01`: (first 2 digits) the camera breaks videos longer than a certain size/length into separate files (see chaptering). Increases by one with each chapter recorded. For example, a 9 minute video would be split into 3 files (`GG010059.MP4`, `GG020059.MP4`, `GG030059.MP4)`.
3. `0059` increases by one with each new video shot (i.e. user stops one video and starts the next). e.g. `GG010059.MP4` and `GG010060.MP4` are two distinct videos.

### Single Photo Burst

The image filename is split into 3 identifying parts (I'll use `G0020061.JPG` as an example):

1. `G0`: always the same. Can be used as a simplistic way to identify a photo in burst photo mode taken on the HERO10 (beware: also used for timelapse)
2. `02`: (first 2 digits) the camera breaks the photos in the burst using the same first digits. e.g. `G0020061.JPG, G0020063.JPG, G0020062.JPG` were all in the same burst. But `G0020061.JPG, G0030062.JPG` are photos from two separate photo burst executions.
3. `0061` increases by one with each photo in the burst.

### Timelapse Video

The video filename is split into 3 identifying parts (I'll use `GX010141.MP4` as an example):

* `GX`: always the same. Can be used as a simplistic way to identify a video in photo liveburst photo mode taken on the HERO10.
* `01`: (first 2 digits) increases by one with each new timelapse shot, or if video reaches chaptering size.
* `0141` increases by one with each new photo in the timelapse

### Timelapse Photo

The image filename is split into 3 identifying parts (I'll use `G0090125.JPG` as an example):

* `G0`: always the same. Can be used as a simplistic way to identify a photo in timelaps mode taken on the HERO10 (beware: also used for single photo burst)
* `02`: (first 2 digits) increases by one with each new timelapse shot
* `0061` increases by one with each new photo in the timelapse

## Video notes

### Video: Activity and Cinematic Modes

These have the same framerates and resolutions as standard mode, except provide different presets for aperture, smoothing, protune, thus changing the visual appearance of the video.

For this reason, only one of each of these samples is included above to illustrate how the filenames of these modes change.

### Video: thm and lrv files

These files are not used by the app, but noted here for reference. These files are created whenever video files are shot on the camera (in any format):

* `.thm` files are JPG thumbnails (THM) used by GoPro software as a still photo preview of the video. They’re tiny files (usually less than 100Kb), typically with a resolution of 160 by 120 pixels.
* `.lrv` files are Low-Resolution Video (LRV) files are used by GoPro software to display video previews, without having to load the high-resolution version.

### Video: GoPro Video Chaptering

Here are the chapter lengths reported by GoPro for the Fusion camera ([https://community.gopro.com/t5/en/GoPro-Camera-File-Chaptering-Information/ta-p/390210](https://community.gopro.com/t5/en/GoPro-Camera-File-Chaptering-Information/ta-p/390210)):

> **HERO10 Black, HERO9 Black, HERO8 Black, MAX, HERO7 Black, HERO6 Black, Fusion, HERO5 Black & HERO5 Session, HERO4 Black & Silver, HERO (2018)**
>
> * Chapter size: approx. 4.0 GB (Samples of HERO9 Black recording times are below)
>   * 5k/30fps High Bitrate is approximately 5 minutes
>   * 1080p/60fps High Bitrate is approximately 7.5 minutes

In our testing we've found that chaptering does indeed happen exactly at 4.01gb. So a maximum of 4.10GB can be assumed.

For one of the highest quality video modes (5.3k @ 30fps w/ Protune) the length of video is 8:53. A maximum of 9:00 can be assumed. See sample: [https://drive.google.com/open?id=1NI55YP7-czsbZdCGMS4yzOulc6AoMKjS](https://drive.google.com/open?id=1NI55YP7-czsbZdCGMS4yzOulc6AoMKjS\&authuser=dgreenwood%40trekview.org\&usp=drive\_fs)

For one of the lowest quality video modes (1080 @ 30fps w/ Protune) the length of the video is 39:24. A maximum of 41:00 can be assumed. See sample: [https://drive.google.com/open?id=1NGsuWaHvF65SYxFOdXEa9hWQlIiwYVYv](https://drive.google.com/open?id=1NGsuWaHvF65SYxFOdXEa9hWQlIiwYVYv\&authuser=dgreenwood%40trekview.org\&usp=drive\_fs)

## Timelapse notes

### Timelapse: Nightlapse Modes

These have the same almost the same frame rates (just a little slower, e.g. no 0.5 sec interval) and resolutions as standard timelapse mode, except provide different presets for aperture, smoothing, protune, designed for low light.

For this reason, only one of each of these samples is included above to illustrate how the filenames of these modes change.