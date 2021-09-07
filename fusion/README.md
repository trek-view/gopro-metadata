# GoPro Fusion Overview

* Manufacturer: GoPro
* Model: MAX
* On Sale: 2017 - 2020

## 360 Modes (suitable for street-level capture)

* Unprocessed Video
	* 360 Video (output .`mp4`)
		* 5.2K stitched (30 FPS)
		* 3k stitched (60 FPS)
* Timelapse photo
	* 360 TimeLapse (output .jpg)
		* 18MP stitched (0.5 sec, 1s, 2s, 5s, 10s, 30s, 60s interval)

[User Manual](/gopro/fusion/Fusion_UM_ENG_REVC.pdf)

### Notes

**Stitching**

GoPro Fusion creates two seperate video files on the memory card. They are named `GPFR` (front camera) or `GPBK` (back camera). Front and back files have the same number ID and are both .mp4 files (e.g. `GPFR0001.mp4` and `GPBK0001.mp4`). The telemetry is stored in the front .mp4. You can tell it is not stitched as it will not contain `XMP-GSpherical:StitchingSoftware` meta.

**.LRV / .THM / .WAV**

When shooting GoPro videos on the Fusion, the camera will also create two .LRV, .THM, files (front and back) and a single .WAV file.

LRV files are low-resolution video files used by GoPros as video previews. THM files are JPG thumbnails used by GoPros as photo previews. Both are used by the GoPro mobile apps. You can safely delete both filetypes — they'll be regenerated from the original MP4 or image file if needed.

.WAV files contain the audio recording from the video.

## Metadata samples

[Download the files here](https://drive.google.com/drive/folders/1QaNr-cfUT4lBYxVoBVe98q_-WH6NAd31?usp=sharing).

[All files contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

#### 360 Video (output .`mp4`)

##### 5.6K stitched @ 30 FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X VIDEO_7152.mp4 > VIDEO_7152.xml
```

###### Output:

[VIDEO_7152.xml](.gopro/max/VIDEO_7152.xml)

###### Validation checks

[For Trek View Explorer](.gopro/fusion/explorer).
