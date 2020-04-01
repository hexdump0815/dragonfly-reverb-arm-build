apt-get install libgl1-mesa-dev
git clone https://github.com/michaelwillis/dragonfly-reverb.git
git checkout 3.0.0
git submodule update --init --recursive
# armv7l
# patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb.armv7l.patch 
# cd dpf ; patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb-dpf.armv7l.patch ; cd ..
# aarch64
# patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb.aarch64.patch 
# cd dpf ; patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb-dpf.aarch64.patch ; cd ..
make
