# 0. Introduction

CAMM is short for Camera Motion Metadata it allows MP4 files to embed metadata about camera motion during video capture.

To first understand `CAMM` we first need to understand what makes an mp4 file. [Understanding Mp4]()

# 1. Metadata

To check if an mp4 video has camm metadata we need to look for the sample entry.

## 1.1. Sample entry

The video file should contain the following sample entry box to indicate the custom metadata track, and the subComponentType of the track should be set to meta.

camm should be stored inside `stsd` container.

here we can look at the structure of a mp4 file where you can see `stsd` holding `camm`

```
     ├── b'trak' [8, 671412]
     │   ├── b'tkhd' [8, 84]
     │   ├── b'edts' [8, 28]
     │   └── b'mdia' [8, 671276]
     │       ├── b'mdhd' [8, 24]
     │       ├── b'hdlr' [8, 52]
     │       └── b'minf' [8, 671176]
     │           ├── b'dinf' [8, 28]
     │           └── b'stbl' [8, 671132]
     │               ├── b'stsd' [8, 24]
     │               │   └── b'camm' [8, 8]
     │               ├── b'stts' [8, 364192]
     │               ├── b'stsc' [8, 66764]
     │               ├── b'stsz' [8, 186360]
     │               └── b'co64' [8, 53752]
     └── b'udta' [8, 221]
         ├── b'\xa9mak' [8, 12]
         ├── b'\xa9mod' [8, 16]
         └── b'meta' [8, 169]
```

Now looking at the `stbl` container, we can see it has `co64` instead of `stco`.The sample table atom can contain a 64-bit chunk offset atom (STChunkOffset64AID = 'co64'). When this atom appears, it is used in place of the original chunk offset atom, which can contain only 32-bit offsets. When QuickTime writes movie files, it uses the 64-bit chunk offset atom only if there are chunks that use the high 32-bits of the chunk offset. Otherwise, the original 32-bit chunk offset atom is used to ensure compatibility with previous versions of QuickTime. 


## 1.2. Camm Metadata

All the information(video, audio or metadata) about the mp4 file is in the mdat atom from where we can get the metadata information.

The metadata track contains a stream of metadata samples.

### 1.2.1. Camm Metadata Samples

Each sample can be identified by intial bytes of the samples.

### 1.2.1.1 Sample Header

uint16 reserved; - Reserved. Should be 0.
uint16 type; - The type of the data packet (see below).

### 1.2.1.1 Data Packets

Each packet has one type of data.

### 1.2.1.1.1 Data Packet (Type 0)

float angle_axis[3]; 

Angle axis orientation in radians representing the rotation from local camera coordinates to a world coordinate system. The world coordinate system is defined by applications.

Let M be the 3x3 rotation matrix corresponding to the angle axis vector. For any ray X in the local coordinate system, the ray direction in the world coordinate is M * X.

This information can be obtained by running 3DoF sensor fusion on the device. After integrating the IMU readings, only the integrated global orientation needs to be recorded.

The three values represent the angle-axis vector, such that the rotation angle in radians is given by the length of the vector, and the rotation axis is given by the normalized vector.

The encoded representation can be created from an axis and angle with float[3] angle_axis := angle_radians * normalized_axis_vec3. A positive angle represents a counterclockwise rotation around the axis.

And the encoded representation can be transformed back to an axis and angle with float[3] axis := normalize(axis_angle) and float angle_radians := length(angle_axis).

### 1.2.1.1.2 Data Packet (Type 1)

int32 pixel_exposure_time;
int32 rolling_shutter_skew_time;


This metadata is per video frame. The presentation time (PTS) of this metadata should be the start of the exposure of the first-used scanline in a video frame.

pixel_exposure_time_ns is the exposure time for a single pixel in nanoseconds and rolling_shutter_skew_time_ns is the delay between the exposure of the first-used scanline and the last-used scanline. They can be used to interpolate per-scanline metadata.

The PTS of the corresponding frame should be within pts_of_this_metadata and pts_of_this_metadata + pixel_exposure_time_ns + rolling_shutter_skew_time_ns.

When this information is not saved, the device should make a best-effort attempt to adjust the PTS of the video frame to be at the center of the frame exposure. 

### 1.2.1.1.3 Data Packet (Type 2)

float gyro[3];

Gyroscope signal in radians/seconds around XYZ axes of the camera. Rotation is positive in the counterclockwise direction.

Applications define the relationship between the IMU coordinate system and the camera coordinate system. We recommend aligning them if possible.

Note that initial gyro readings are in the IMU coordinate system defined by its driver, and proper transformation is required to convert it to the camera coordinate system. 

### 1.2.1.1.4 Data Packet (Type 3)

float acceleration[3];

Accelerometer reading in meters/second^2 along XYZ axes of the camera.

Applications define the relationship between the IMU coordinate system and the camera coordinate system. We recommend aligning them if possible. 

### 1.2.1.1.5 Data Packet (Type 4)

float position[3];

3D position of the camera. 3D position and angle axis rotation together defines the 6DoF pose of the camera, and they are in a common application-defined coordinate system.

You can get this information by running 6DoF tracking on the device.

### 1.2.1.1.6 Data Packet (Type 5)

double latitude;
double longitude;
double altitude;


Minimal GPS coordinate of the sample.

### 1.2.1.1.7 Data Packet (Type 6)

double time_gps_epoch;
int gps_fix_type;
double latitude;
double longitude;
float altitude;
float horizontal_accuracy;
float vertical_accuracy;
float velocity_east;
float velocity_north;
float velocity_up;
float speed_accuracy;

time_gps_epoch - Time since the GPS epoch when the measurement was taken
gps_fix_type - 0 ( no fix), 2 (2D fix), 3 (3D fix)
latitude - Latitude in degrees
longitude - Longitude in degrees
altitude - Height above the WGS-84 ellipsoid
horizontal_accuracy - Horizontal (lat/long) accuracy
vertical_accuracy - Vertical (altitude) accuracy
velocity_east - Velocity in the east direction
velocity_north - Velocity in the north direction
velocity_up - Velocity in the up direction
speed_accuracy - Speed accuracy 

### 1.2.1.1.8 Data Packet (Type 7)

float magnetic_field[3];

Ambient magnetic field.

### 1.2.2. Extracting Camm Metadata Samples
Now we can get the metdata by querying the offsets from `co64` using `stsz` for respective sizes.

as we can see that for every offset our size are always `16` which can't hold all the camm metadata, so to get all the metadata we can check the `stsc` to check how many chunks are there for the respective offset.

so if we look at the last offset we get the value `69` which means we have 69 chunks of data of size `16`.

Now, if we query the last offset we get,

- b'\x00\x00\x02\x00\xf3\x89\xde\xbca\x9d\xef<\\BN\xba' - `\x00\x00` = 0, `\x00\x02` = 2
- b'\x00\x00\x03\x0033\x89>33:>\xcd\xbb"A'  - `\x00\x00` = 0, `\x00\x03` = 2 etc.
.
.
.
- b'\x00\x00\x06\x00\x00\x00\xc0\x0fm\xa1\xd7A\x03\x00\x00\x00'

now if we check `\x00\x00` which equals to `0` and `\x06\x00` which equals to `6`

so now we can see the pattern which equates to how camm metadata should look like.

now to read the actual data, we can see that `6` value is for gps related information.

```
    double time_gps_epoch;
    int gps_fix_type;
    double latitude;
    double longitude;
    float altitude;
    float horizontal_accuracy;
    float vertical_accuracy;
    float velocity_east;
    float velocity_north;
    float velocity_up;
    float speed_accuracy;
```

Now if we read the data as per specification, we got:

```
2020-04-02 09:45:35
3
50.456223
30.479778333333336
147.89999389648438
1.100000023841858
1.100000023841858
-0.029577525332570076
0.010508677922189236
0.0
0.0
```

which surely looks like expected data.

let use equate for better readability:

```
    double time_gps_epoch = 2020-04-02 09:45:35; // GPSDateTime
    int gps_fix_type = 3; // GPSMeasureMode = 3-Dimensional Measurement
    double latitude = 50.456223; // GPSLatitude
    double longitude = 30.479778333333336; // GPSLongitude
    float altitude = 147.89999389648438; // GPSAltitude
    float horizontal_accuracy = 1.100000023841858; // GPSHorizontalAccuracy
    float vertical_accuracy = 1.100000023841858; // GPSVerticalAccuracy
    float velocity_east = -0.029577525332570076; // GPSVelocityEast
    float velocity_north = 0.010508677922189236; // GPSVelocityNorth
    float velocity_up = 0.0; // GPSVelocityUp
    float speed_accuracy = 0.0; // GPSSpeedAccuracy
```

Like this we can query all the offsets to get the related metadata.

To check the `latitude` and `longitude` values in dms value, please check below function described in the below stackoverflow link.

#https://stackoverflow.com/questions/2579535/convert-dd-decimal-degrees-to-dms-degrees-minutes-seconds-in-python/2580236#2580236
def decdeg2dms(dd):
    mult = -1 if dd < 0 else 1
    mnt,sec = divmod(abs(dd)*3600, 60)
    deg,mnt = divmod(mnt, 60)
    return mult*deg, mult*mnt, mult*sec

# 1.3. Injecting Camm Metadata

Using above information we can also be able to inject the camm data to the video.

First we need to create the samples as per requirements and then we can simply inject them in the video.

All the samples will go in the `mdat atom` with file offset in `co64`, sizes in `stsz`, chunks information in `stsc` and time information in `stts`.

Also there should be a camm track atom inside `stsd` atom as described in [1.1. Sample Entry]()

# 1.4. Notes

- There should be only one CAMM track per MP4 file, which contains all of the above data types by muxing them together.
- GPS samples in cases 5 and 6 must be raw values generated by sensors. They can not be interpolated or repeated when there is no GPS change.
- The coordinate systems are right-hand sided. The camera coordinate system is defined as X pointing right, Y pointing downward, and Z pointing forward. The Y-axis of the global coordinate system should point down along the gravity vector.
- IMU readings are typically in a separate IMU coordinate system, and rotation is needed to map them to the camera coordinate system if the two coordinate systems are different.
- All fields are little-endian (least significant byte first), and the 32-bit floating points are of IEEE 754-1985 format.
- To accurately synchronize the video frame and the metadata, the PTS of the video frame should be at the center of its exposure (this can also be inferred from exposure metadata).
The application muxing this data should choose a large enough time scale to get an accurate PTS.



# 1.5. Tips for capturing 360 videos for Street View

You can help us optimize how your imagery looks on Google Maps by following these tips when capturing 360 videos for Street View. It may take time for blue lines to appear after imagery is published; Google may also reprocess imagery positioning from time to time. These processes generally complete within 48 hours.

Tip: Street View is not currently available for videos collected indoors.
How to position and set up your camera

    Remember to disable any gyroscopic stabilization.
    Keep your camera upright and as high above your camera support system as possible.
    Try to position your camera support system so that it takes up less than 25% of the bottom of the resulting 360 image. You can check this if your camera supports a real-time preview.
    Consider the lighting of your environment (e.g. avoid sunrise/sunset, adjust exposure for bright conditions). If your camera supports a real-time preview, you can use signs and storefronts to verify proper exposure.
    Consider using available tools from the manufacturer, like a mobile app, to control the camera.

## 1.5.1. Additional tips

    If supported by your camera, consider setting the frame rate to 5 frames per second at driving or biking speeds and 1 frame per second for walking speeds.
    To ensure that GPS data is properly collected, start and stop your collection path in areas with open sky (e.g. avoid trees, buildings, etc.). Videos collected indoors or inside tunnels often lack adequate GPS and may not publish successfully.
    Make sure there are no long time gaps (>5 seconds) between GPS samples.
    Check that your GPS samples aren't impossible: if latitude and longitude jump all over the place in ways that a car or person could never achieve, we may reject the video.
    To help us automatically position 360 images in relation to one another, when capturing imagery, try to overlap with some areas you already captured in the collection. This include turns (e.g. a city block) in your collection path.
    Try to limit your speed to:
        Under 5 mph or 8 kmh when capturing at 1fps
        Under 30 mph or 45 kmh when capturing at 5fps
        Under 45 mph or 70 kmh when capturing at 7fps
    If processing is required after capturing a video, the same fps setting must be used. 
    Try to record your 360 videos for at least 2 minutes but for no longer than 60 minutes at a time (unless otherwise advised by the camera manufacturer).


# 1.5. Errors

- Video is too short
- Video does not contain more than 10 GPS points.
- Make sure there are no long time gaps (>5 seconds) between GPS samples.
- GPS data jumps around a lot
- GPS timestamps do not overlap with Video timestamps




