# Maker Land 2016 Radio Workshop

This repo contains a bunch of utilities used during my Radio Workshop at Maker Land 2016, gathered into one place for ease of use:


    git clone --recursive https://github.com/natevw/makerland-radio.git
    cd makerland-radio
    #git submodule update --init    # (if you forgot --recursive above)


We'll be receiving on a laptop or other computer with display, and transmitting from some Raspberry Pis on the network — so clone this repo (recursively) to both your laptop and on the "radiopi" you are accessing.

To get transmitter stuff ready:

    N=42
    ssh pi@radiopi$N.local
    # password is the Raspian default: raspberry
    
    # clone the repo as above
    cd rpitx
    ./install.sh

To build receiver DSP stuff:
    
    
    # OS X
    cd csdr-osx
    # edit Makefile, modify second `PARAMS_LIBS` line to read:
    #    PARAMS_LIBS = -g -lm -I/usr/local/include -L/usr/local/lib -lfftw3f -DUSE_FFTW -DLIBCSDR_GPL -DUSE_IMA_ADPCM
    make
    ln -s /Applications/Gqrx.app/Contents/MacOS/rtl_sdr /usr/local/bin/rtl_sdr
    
    # Linux [not directly tested]
    cd csdr   # or csdr-osx if on macoS
    make
    
    # following http://gqrx.dk/download/install-ubuntu and rtl_sdr should theoretically also get installed

Thanks to [NooElec](http://www.nooelec.com/) for loaning us a bunch of [NESDR Smart kits](https://www.amazon.com/NooElec-NESDR-SMArt-Enclosure-R820T2-Based/dp/B01GDN1T4S) for this workshop!