# V4L Video Test Application

## 1. What Is This ?

This is a simple video test application which uses Linux V4L interfaces to simulate several basic Encoder and Decoder behaviors. The main purpose of this test application is to test the compatibility and validity of video drivers on Unix-like operating systems.

## 2. How To Build This Project ?

This project requires a few opensource dependencies for compilation and execution :

1. [**FFMpeg**](https://git.ffmpeg.org/ffmpeg.git) - used as input demuxer.
2. [**JsonCpp**](https://github.com/open-source-parsers/jsoncpp) -  used as configuration parser.

### 2.1. Setup Development Environment

To compile this project we need to setup the compiling environment for ARM architecture.

```bash
sudo apt-get -y install cmake g++ pkg-config
```

### 2.2 Install dependent packages

```bash
sudo apt-get -y install libavcodec-dev libavformat-dev libavutil-dev libswscale-dev libjsoncpp-dev
```

### 2.3 Build & Test The Project

```bash
cd v4l-video-test-app
mv CMakeLists.ubuntu.txt CMakeLists.txt
cmake -B build .
make
```

#### Give newly created binary iris_v4l2_test executable rights
```bash
cd build/
chmod +x iris_v4l2_test
```

#### 2.3.2 Follow the below commands to run the tests

##### This commands helps in understanding the requirement and options for running the test
```bash
./iris_v4l2_test --help
```

##### Command to run the Encoder testcase.
```bash
./iris_v4l2_test --config ./data/config/h264Encoder.json
```
##### Command to run the Decoder testcase.
```bash
./iris_v4l2_test --config ./data/config/h264Decoder.json
```

##### Command to run the testcase with custom log level. Range: [0, 16]
```bash
./iris_v4l2_test --loglevel 12 --config ./data/config/h264Decoder.json
```
