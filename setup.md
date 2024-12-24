# Setup

Instructions for downlaoding and compiling redox.

## Podman Method

The Podman method builds redox inside a docker like container.

Follow instructions from here: 
https://doc.redox-os.org/book/podman-build.html

Basically, download the build script:
curl -sf https://gitlab.redox-os.org/redox-os/redox/raw/master/podman_bootstrap.sh -o podman_bootstrap.sh

and run it:
time bash -e podman_bootstrap.sh

## Launch Redox in Qemu

To launch into Orbital (the default UI):
make qemu

TO launch straight into a terminal:
make qemu gpu=no