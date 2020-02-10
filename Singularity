BootStrap: docker
From: ubuntu:18.04

%labels
    Maintainer zyou@osc.edu
    Recipe https://github.com/OSC/sa_singularity_winehq

%post
    apt update
    apt upgrade -y
    dpkg --add-architecture i386 
    DEBIAN_FRONTEND=noninteractive apt install -y software-properties-common wget
    wget -nc https://dl.winehq.org/wine-builds/winehq.key
    apt-key add winehq.key

    apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main'
    apt update
    # https://askubuntu.com/questions/1145473/how-do-i-install-libfaudio0 
    # Beginning with Wine 4.5 the wine-devel packages from WineHQ require libfaudio0 as a dependency.
    wget -nc https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/amd64/libfaudio0_19.07-0~bionic_amd64.deb
    wget -nc https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/i386/libfaudio0_19.07-0~bionic_i386.deb
    dpkg -i libfaudio0_19.07-0~bionic_amd64.deb libfaudio0_19.07-0~bionic_i386.deb || true
    DEBIAN_FRONTEND=noninteractive apt install -f -y
    DEBIAN_FRONTEND=noninteractive apt install -y winehq-stable=5.0.0~bionic

    # Clean up
    apt autoclean
    apt autoremove --purge -y
    rm -rf /var/lib/apt/lists/*

%runscript
    exec wine64 "$@"
