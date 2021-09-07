# GoPro MAX Overview

* Manufacturer: GoPro
* Model: MAX
* On Sale: 2019 - Present

## 360 Modes (suitable for street-level capture)

* Unprocessed Video
	* 360 Video (output .`360`)
		* 5.6K stitched (24FPS, 30FPS)
		* 3k stitched (60 FPS)
	* 360 TimeWarp (output `.360`)
		* (2x,5x,10x,15x,30x frame rate)
* Timelapse photo
	* 360 TimeLapse 360 (output .jpg)
		* 16.6MP stitched (2s, 5s, 10s, 30s, 60s interval)

[User Manual](/MAX_UM_ENG_REVA.pdf)

### Notes

**.360's**

All videos shot on the MAX are stitched as `.360` files on the camera. This is a propriatory GoPro format (with EAC projection). [Using GoPro Player](https://community.gopro.com/t5/en/GoPro-Player/ta-p/413305) you can convert to mp4 (with equirectanguar projection).

**.LRV / .THM**

When shooting GoPro videos on the MAX, the camera will also create .LRV and .THM files.

LRV files are low-resolution video files used by GoPros as video previews. THM files are JPG thumbnails used by GoPros as photo previews. Both are used by the GoPro mobile apps. You can safely delete both filetypes — they'll be regenerated from the original MP4 or image file if needed.

## Metadata samples

[Download the files here](https://drive.google.com/drive/folders/1T2-ntDGtvBJlgDOmNwrKAQfvkP8leIQD?usp=sharing).

[All files contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

### Unprocessed Videos (.360)

The GoPro MAX writes .360 files to the SD card. .360 is a GoPro proprietary format. .360's use EAC projections.

Video file names are preface with `GS` and increase sequentially numerically based on existing files on memory card (e.g. `GS018423.360`, `GS018424.360`.

When shooting video longer than 8 mins (about 4GB), GoPro creates a new .360 file (put another way; .360 video files are chunked into 8min/4gb outputs).

#### 360 Video (output .`360`)

##### 5.6K stitched @ 24FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018422.360 > GS018422.xml
```

###### Output:

[GS018422.xml](/GS018422.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

##### 5.6K stitched @ 30FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018421.360 > GS018421.xml
```

###### Output:

[GS018421.xml](/GS018421.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

##### 3K stitched @ 60FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018423.360 > GS018423.xml
```

###### Output:

[GS018423.xml](/GS018423.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

##### TimeWarp @ 5.6k

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018424.360 > GS018424.xml
```

###### Output:

[GS018424.xml](/GS018424.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

---

### Processed Videos (.mp4)

User need to convert .360's into a more available standard using [GoPro Studio](https://community.gopro.com/t5/en/GoPro-Player/ta-p/413305). This software allows for some video adjustments (e.g. horizon leveling) during processing. Outputted mp4's use equirectangular projections.

Note: the GPMF metadata (telemetry) is not retained on the Windows version of GoPro Studio.

The files used here were stitched on a Mac in h264 with no additional setting enabled (e.g. Horizon levelling).

##### 5.6K stitched @ 24FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018422.mp4 > GS018422_mp4.xml
```

###### Output:

[GS018422_mp4.xml](GS018422_mp4.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

##### 5.6K stitched @ 30FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018421.mp4 > GS018421_mp4.xml
```

###### Output:

[GS018421_mp4.xml](/GS018421_mp4.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

##### 3K stitched @ 60FPS

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018423.mp4 > GS018423_mp4.xml
```

###### Output:

[GS018423_mp4.xml](/GS018423_mp4.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

##### TimeWarp @ 5.6k

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018424.mp4 > GS018424_mp4.xml
```

###### Output:

[GS018424_mp4.xml](/GS018424_mp4.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).

---

### Timelapse photo (.jpg)

360 .jpgs are stitched on camera.

Timelapse file names are preface with `GS` . Each unique timelapse is prefaced with two characters starting at AA, and increase sequentially alphabetically based on existing timelapses on memory card (e.g. `GSAA`, `GSAB`. Each photo in timelapse is assigned a number starting at 0001. The next timelapse photo follows the same sequential numerical order (e.g. GSAA0001.jpg - GSAA0991.jpg, GSAB0992.jpg - GSAB2001.jpg).

##### 16.6mp output

###### Input:

```
exiftool -X GSAD3685.JPG > GSAD3685.xml
```

###### Output:

[GSAD3685.JPG](/GSAD3685.xml)

###### Validation checks

[For Trek View Explorer](/explorer.md).