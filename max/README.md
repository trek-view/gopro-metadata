# GoPro MAX Overview

* Manufacturer: GoPro
* Model: MAX
* On Sale: 2019 - Present
* [User Manual](/MAX_UM_ENG_REVA.pdf)

## Modes 

### 360 Modes

* Unprocessed Video
	* 360 Video (output .`360`)
		* [5.6K stitched (24FPS)](#56k-stitched--24fps-output-360)
		* [5.6K stitched (30FPS)](#56k-stitched--30fps-output-360)
		* [3k stitched (60 FPS)](#3k-stitched--60fps-output-360)
	* 360 TimeWarp stitched (output `.360`)
		* [2x rate](#timewarp-stitched--56k-2x-output-360)
		* [5x rate](#timewarp-stitched--56k-5x-output-360)
		* [10x rate](#timewarp-stitched--56k-10x-output-360)
		* [15x rate](#timewarp-stitched--56k-15x-output-360)
		* [30x rate](#timewarp-stitched--56k-30x-output-360)
* Processed Video (output of GoPro Studio)
	* 360 Video (output `.mp4`)
		* [5.6K stitched (24FPS)](#56k-blended--24fps-output-mp4)
		* [5.6K stitched (30FPS)](#56k-blended--30fps-output-mp4)
		* [4K stitched ()]()
		* [3k stitched (60 FPS)](#3k-blended--60fps-output-mp4)
	* 360 TimeWarp stitched (output `.mp4`)
		* [5x rate](#timewarp-blended--56k-output-mp4)
	* HERO Video (output `.mp4`)
		* [1440 @60 FPS](#1440-60-fps-output-mp4)
		* [1080 @60 FPS](#1080-60-fps-output-mp4)
		* [1080 @60 FPS Max SuperView](#1080-60-fps-max-superview-output-mp4)
	* HERO Timewarp 1080 Auto (output `.mp4`)
		* [Auto frame rate](#timewarp-1080-auto-output-mp4)
* Timelapse photo
	* 360 TimeLapse 360 (output `.jpg`)
		* [16.6MP stitched (2s, 5s, 10s, 30s, 60s interval)](x#166mp-output-output-jpg)
	* HERO Photo (output `.jpg`)
		* [1080 output (wide)](#1080-output-wide-output-jpg)

### Notes

#### .360's

All videos shot on the MAX are stitched as `.360` files on the camera. This is a propriatory GoPro format (with EAC projection). [Using GoPro Player](https://community.gopro.com/t5/en/GoPro-Player/ta-p/413305) you can convert to mp4 (with equirectanguar projection).


#### Download Samples

[Download the all the samples here](https://drive.google.com/drive/folders/1T2-ntDGtvBJlgDOmNwrKAQfvkP8leIQD?usp=sharing).

[All files in this analysis contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

## Metadata Samples

### Unprocessed Videos

The GoPro MAX writes `.360` files to the SD card. `.360` is a GoPro proprietary format. .360's use EAC projections.

Video file names are preface with `GS` and increase sequentially numerically based on existing files on memory card (e.g. `GS018423.360`, `GS018424.360`.

When shooting video longer than 8 mins (about 4GB), GoPro creates a new .360 file (put another way; .360 video files are chunked into 8min/4gb outputs).

#### 360 Video

##### 5.6K stitched @ 24FPS (output `.360`)

* [GS018422.xml](/max/GS018422.xml)
* Telemetry: Track4

##### 5.6K stitched @ 30FPS (output `.360`)

* [GS018421.xml](/max/GS018421.xml)
* Telemetry: Track4

##### 3K stitched @ 60FPS (output `.360`)

* [GS018423.xml](/max/GS018423.xml)
* Telemetry: Track4

##### TimeWarp stitched @ 5.6k 2x (output `.360`)

* [GS018469.xml](/max/GS018469.xml)
* Telemetry: Track3

##### TimeWarp stitched @ 5.6k 5x (output `.360`)

* [GS018424.xml](/max/GS018424.xml)
* Telemetry: Track3

##### TimeWarp stitched @ 5.6k 10x (output `.360`)

* [GS018470.xml](/max/GS018470.xml)
* Telemetry: Track3

##### TimeWarp stitched @ 5.6k 15x (output `.360`)

* [GS018471.xml](/max/GS018471.xml)
* Telemetry: Track3

##### TimeWarp stitched @ 5.6k 30x (output `.360`)

* [GS018472.xml](/max/GS018472.xml)
* Telemetry: Track3

### Processed Videos

#### 360 Video

Users can convert `.360`'s into a more available standard using [GoPro Studio](https://community.gopro.com/t5/en/GoPro-Player/ta-p/413305). This software allows for some video adjustments (e.g. horizon leveling) during processing. Outputted mp4's use equirectangular projections.

Note: the GPMF metadata (telemetry) is not retained on the Windows version of GoPro Studio.

The files used here were stitched on a Mac in h264 with no additional setting enabled (e.g. Horizon levelling).

##### 5.6K stitched @ 24FPS (output `.mp4`)

* [GS018422_mp4.xml](/max/GS018422_mp4.xml)
* Telemetry: Track3

##### 5.6K stitched @ 30FPS (output `.mp4`)

* [GS018421_mp4.xml](/max/GS018421_mp4.xml)
* Telemetry: Track3

##### 3K stitched @ 60FPS (output `.mp4`)

* [GS018423_mp4.xml](/max/GS018423_mp4.xml)
* Telemetry: Track3

#### 360 Timewarp @ 5.6k 2x

* [GS018424_mp4.xml](/max/GS018424_mp4.xml)
* Telemetry: Track2

#### HERO Video

##### 1440 @60 FPS (output .`mp4`)

* [GH018429_mp4.xml](/max/GH018429_mp4.xml)
* Telemetry: Track4

##### 1080 @60 FPS (output .`mp4`)

* [GH018429_mp4.xml](/max/GH018427_mp4.xml)
* Telemetry: Track4

##### 1080 @60 FPS Max SuperView (output .`mp4`)

* [GH018429_mp4.xml](/max/GH018428_mp4.xml)
* Telemetry: Track4

#### HERO Timewarp

Timewarps can be set at a number of framerates from 2x to 60x (or auto, where GoPro decides best rate)

##### Timewarp 1080 Auto (output .`mp4`)

* [GH018429_mp4.xml](/max/GH018426_mp4.xml)
* Telemetry: Track4

---

### Timelapse photo (.jpg)

#### 360 Timelapse

Spherical .jpgs are stitched on camera.

Timelapse file names are preface with `GS` . Each unique timelapse is prefaced with two characters starting at AA, and increase sequentially alphabetically based on existing timelapses on memory card (e.g. `GSAA`, `GSAB`. Each photo in timelapse is assigned a number starting at 0001. The next timelapse photo follows the same sequential numerical order (e.g. GSAA0001.jpg - GSAA0991.jpg, GSAB0992.jpg - GSAB2001.jpg).

##### 16.6mp output (output `.jpg`)

* [GSAD3685.JPG](/max/GSAD3685.xml)

#### HERO Timelapse photo 

.jpgs are stitched on camera.

Timelapse file names are preface with `GP` . Each unique timelapse is prefaced with two characters starting at AA, and increase sequentially alphabetically based on existing timelapses on memory card (e.g. `GPAA`, `GPAB`. Each photo in timelapse is assigned a number starting at 0001. The next timelapse photo follows the same sequential numerical order (e.g. GPAA0001.jpg - GPAA0991.jpg, GPAB0992.jpg - GPAB2001.jpg).

##### 1080 output (wide) (output `.jpg`)

* [GSAD3685.JPG](/max/GPAA8441.xml)