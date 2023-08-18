# GoPro MAX Overview

* Manufacturer: GoPro
* Model: MAX
* On Sale: 2019 - Present

# GoPro Max Camera Modes

## Overview of MAX workflow

360/HERO Images are captured on the camera, stitched as jpgs.

360 videos are captured on the camera as .360 files (which is a propriety GoPro format). GoPro Player can be used to convert 360's in to more widely understood equirectangular mp4s). More here: [https://www.trekview.org/blog/2021/reverse-engineering-gopro-360-file-format-part-1/](https://www.trekview.org/blog/2021/reverse-engineering-gopro-360-file-format-part-1/)&#x20;

HERO videos are captured on the camera as .mp4 files.&#x20;

## File Naming Conventions

### Video: 360 Mode (.360)

The video filename is split into 3 identifying parts (I'll use `GS010135.360` as an example):

1. `GS`: always the same. Can be used as a simplistic way to identify a 360 video taken on the MAX.
2. `01`: (first 2 digits) the camera breaks videos longer than a certain size/length into separate files ([see chaptering](gopro-max-camera-modes.md#gopro-video-chaptering)). Increases by one with each chapter recorded. For example, a 19 minute video would be split into 3 files (`GS010135.360`, `GS020135.360`, `GS030135.360)`.
3. `0135` increases by one with each new video shot (i.e. user stops one video and starts the next). e.g. `GS010135.360` and `GS010136.360` are two distinct videos.

### Video: 360 Mode (.mp4)

Same as the .360. Only thing worth noting is the mp4 video filename (outputted by GoPro Player) is the same as the .360 version (e.g. `GS010135.360` becomes `GS010135.mp4` after stitching).

### Video: Hero Mode (.mp4)

The video filename is split into 3 identifying parts (I'll use `GL010135.mp4` as an example):

1. `GL`: always the same. Can be used as a simplistic way to identify a HERO video taken on the MAX.
2. `01`: (first 2 digits) the camera breaks videos longer than a certain size/length into separate files ([see chaptering](gopro-max-camera-modes.md#gopro-video-chaptering)). Increases by one with each chapter recorded. For example, a 19 minute video would be split into 3 files (`GL010135.mp4`, `GL020135.mp4`, `GL030135.mp4)`.
3. `0135` increases by one with each new video shot (i.e. user stops one video and starts the next). e.g. `GL010135.mp4` and `GL010136.mp4` are two distinct videos.

### Single Photo: 360 Photo Mode <a href="#single-photo-360-photo-mode" id="single-photo-360-photo-mode"></a>

The image filename is split into 2 identifying parts (I'll use `GS__8588.JPG` as an example):

1. `GS__` : always the same. Can be used as a simplistic way to identify an equirectangular photo taken on the MAX in single photo mode
2. `8588:` count of the photo (increments by 1 each time between 0000 - 9999)

### Single Photo: HERO Photo Mode <a href="#single-photo-hero-photo-mode" id="single-photo-hero-photo-mode"></a>

The image filename is split into 2 identifying parts (I'll use `GP__8586.JPG` as an example):

1. `GP__` : always the same. Can be used as a simplistic way to identify a HERO photo taken on the MAX in single photo mode
2. `8586:` count of the photo (increments by 1 each time between 0000 - 9999)

### Timelapse Photo: 360 Mode (photo)

The image filename is split into 3 identifying parts (I'll use `GSAF8427.JPG` as an example):

1. `GS`: always the same. Can be used as a simplistic way to identify a 360 photo taken on the MAX un timelapse mode.
2. `AF`: (first 2 letters) the camera breaks down each time photo invoked. Increases by one with each button press.  (i.e. user takes one photo and captures the next). e.g. `GSAF8427.jpg` and `GSAG8428.jpg` are two distinct photos. In the case of timelapse, might have many photos with same two letter code (e.g. `GSAF8427.JPG, GSAF8428.JPG, ...)`
3. `8427` increases by one with each photo. In timelapse that would be `GSAF8427.JPG, GSAF8428.JPG` or just shooting photos manually would be `GSAF8427.JPG GSAG8428.JPG`

### Timelapse Photo: 360 Mode (video + timewarp)

Same as Video: 360 video mode

### Timelapse Photo: HERO Mode (photos)

The image filename is split into 3 identifying parts (I'll use `GPAA1001.JPG` as an example):

1. `GP`: always the same. Can be used as a simplistic way to identify a HERO timelapse photo taken on the MAX in timelapse mode
2. `AA`: (first 2 letters): same behaviour as describer in previous section: MAX 360 Photos (equirectangular)
3. `1001`: same behaviour as describer in previous section: MAX 360 Photos (equirectangular)

### Timelapse Photo: HERO Mode (video + timewarp)

The image filename is split into 3 identifying parts (I'll use `GH018714.mp4` as an example):

1. `GH`: always the same. Can be used as a simplistic way to identify a HERO timelapse photo taken on the MAX in timelapse mode
2. `01`: (first 2 digits) the camera breaks videos longer than a certain size/length into separate files ([see chaptering](gopro-max-camera-modes.md#gopro-video-chaptering)). Increases by one with each chapter recorded. For example, a 19 minute video would be split into 3 files (`GH018714.mp4`, `GH028714.mp4`, `GH3018714.mp4)`.
3. `8714` increases by one with each new video shot (i.e. user stops one video and starts the next). e.g. (`GH018714.mp4` and `GH018715.mp4` are two distinct videos.

## Video notes

### Video: Notes on upscaling

Note 1: it appears both 5.6k and 3k selected resolutions are both upscaled from raw 360 files. Seems like 5.6k .360 is actually 4k.

Note 2: for each input resolution GoPro offers the above listed standard resolution outputs. User is also free to choose "custom" resolution in GP Player, but for our use-cases we completely ignore (through upload validation) that processed mp4 is created using a default GP Player resolution.

![](https://raw.githubusercontent.com/trek-view/gopro-metadata/notes/images/max-upscaling.png)

### Video: thm and lrv files

These files are not used by the app, but noted here for reference. These files are created whenever video files are shot on the camera (in any format):

* `.thm` files are JPG thumbnails (THM) used by GoPro software as a still photo preview of the video. They’re tiny files (usually less than 100Kb), typically with a resolution of 160 by 120 pixels.
* `.lrv`  files are Low-Resolution Video (LRV) files are used by GoPro software to display video previews, without having to load the high-resolution version.

### Video: GoPro Video Chaptering

Here are the chapter lengths for each camera reported by GoPro ([https://community.gopro.com/t5/en/GoPro-Camera-File-Chaptering-Information/ta-p/390210](https://community.gopro.com/t5/en/GoPro-Camera-File-Chaptering-Information/ta-p/390210)):

> **HERO10 Black, HERO9 Black, HERO8 Black, MAX, HERO7 Black, HERO6 Black, Fusion, HERO5 Black & HERO5 Session, HERO4 Black & Silver, HERO (2018)**
>
> * Chapter size: approx. 4.0 GB (Samples of HERO9 Black recording times are below)
>   * 5k/30fps High Bitrate is approximately 5 minutes
>   * 1080p/60fps High Bitrate is approximately 7.5 minutes

On the MAX the raw .360 video produced is never greater than 4.2GB shot at 5.6k (24fps) resolution. This results in no more than 8:30 worth of video footage. When stitched at H264 mp4 at 5.6k resolution the filesize can almost double, but is never more than 7.5GB.

When shot at 30fps in 5.6k mode, the output filesize is the same, but video content is abit shorted at just over 8 minutes worth of vide.

In 3k mode at 60fps the output filesize produced for the .360 is never mode than 3.9GB, but resultant footage is much longer -- up to 13 minutes 30 seconds of content.&#x20;

In HERO mode at 1080 60FPS / 1440 60FPS the files reaches 4gb before chaptering, and is no more than 9 minutes long.

## Timelapse Notes

### Timelapse photo: Notes on Timewarp

Timewarp increases the speed (by up to 30x original speed) to turn long recordings into shorter movies.