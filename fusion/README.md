# GoPro Fusion Overview

* Manufacturer: GoPro
* Model: Fusion
* On Sale: 2017 - 2020

## 360 Modes (suitable for street-level capture)

* Processed Video
	* 360 Video (output .`mp4`)
		* 5.2K stitched (30 FPS)
		* 3k stitched (50 FPS, PAL)
		* 3k stitched (60 FPS, NTSC)
* Timelapse photo
	* 360 TimeLapse (output .jpg)
		* 18MP stitched (0.5 sec, 1s, 2s, 5s, 10s, 30s, 60s interval)

[User Manual](/Fusion_UM_ENG_REVC.pdf)

### Notes

**.LRV / .THM / .WAV**

When shooting GoPro videos on the Fusion, the camera will also create two .LRV, .THM, files (front and back) and a single .WAV file.

LRV files are low-resolution video files used by GoPros as video previews. THM files are JPG thumbnails used by GoPros as photo previews. Both are used by the GoPro mobile apps. You can safely delete both filetypes — they'll be regenerated from the original MP4 or image file if needed.

.WAV files contain the audio recording from the video.

**Times**

One important point to note: `CreateDate` fields in metadata refer to the time the image was stitched. When stitching is done on a PC, the reported `CreateDate` can therefore differ significantly from the actual time the imagery was captured. In many cases it is therefore more accurate to rely on the reported `GPSDateTime` values for true capture times.

## Metadata samples

[Download the files here](https://drive.google.com/drive/folders/1QaNr-cfUT4lBYxVoBVe98q_-WH6NAd31?usp=sharing).

[All files contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

### 360 Video (output .`mp4`)

GoPro Fusion creates two seperate video files on the memory card. They are named `GPFR` (front camera) or `GPBK` (back camera). Front and back files have the same number ID and are both .mp4 files (e.g. `GPFR0001.mp4` and `GPBK0001.mp4`). The telemetry is stored in the front .mp4. You can tell it is not stitched as it will not contain `XMP-GSpherical:StitchingSoftware` meta.

##### 5.6K stitched @ 30 FPS

* [VIDEO_7152.xml](/VIDEO_7152.xml)
* Telemetry: Track3

##### 3K stitched at 50FPS (PAL)

* [VIDEO_8806.xml](/fusion/VIDEO_8806.xml)
* Telemetry: Track3

##### 3K stitched at 60FPS (NTSC)

* [VIDEO_8807.xml](/fusion/VIDEO_8807.xml)
* Telemetry: Track3

---

### Timelapse photo (.jpg)

GoPro Fusion creates two seperate image files (front and back) on the memory card. 

Stitched timelapse file names are preface with `MULTISHOT_` . Each unique timelapse is prefaced with a 4 digit number, which takes the last 4 digits of photo filenames before stitched (e.g. GF089146.JPG and GB089146.JPG = MULTISHOT_9146_xxxxxx.jpg. xxxxxx represents number of timelapse in sequence, starting with 000000 (e.g. MULTISHOT_9146_000000.jpg).

Note, GoPro Fusion prestitched files follow an order where timelapse is defined by the first 2 digits (e.g GF08, GF09, GF10).

You can tell it is not stitched as it will not contain `XMP-GPano:StitchingSoftware` meta.

##### 16.6mp output

* [MULTISHOT_9146_000000.jpg](/MULTISHOT_9146_000000.xml)