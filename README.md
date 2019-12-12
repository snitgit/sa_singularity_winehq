# Singularity WineHQ

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/3891)
[![GitHub License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

Singularity image for [WineHQ](https://www.winehq.org/). It was built on top of the base Docker image [ubuntu](https://hub.docker.com/_/ubuntu).

## Build

You can build a local Singularity image named `winehq.sif` with:

```sh
sudo singularity build winehq.sif Singularity
```

## Deploy

Instead of building it yourself you can download the pre-built image from [Singularity Hub](https://www.singularity-hub.org) with:

```sh
singularity pull winehq.sif shub://OSC/sa_singularity_winehq
```

## Run

### Run 64-bit Windows binary
WineHQ is started using the default run command:
```sh
singularity run winehq.sif /path/to/windows_64bit_exe
```
or as a native command
```sh
./winehq.sif /path/to/windows_64bit_exe
```

### Run 32-bit Windows binary
```sh
singularity exec winehq.sif exec wine /path/to/windows_32bit_exe
```

## License

The code is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
