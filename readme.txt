apt-get install libgl1-mesa-dev
git clone https://github.com/michaelwillis/dragonfly-reverb.git
cd dragonfly-reverb
git checkout 3.0.0
git submodule update --init --recursive
# armv7l
# patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb.armv7l.patch 
# cd dpf ; patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb-dpf.armv7l.patch ; cd ..
# aarch64
# patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb.aarch64.patch 
# cd dpf ; patch -p1 < /compile/doc/dragonfly-reverb/dragonfly-reverb-dpf.aarch64.patch ; cd ..
make

mkdir -p /usr/local/lib/vst
for i in DragonflyEarlyReflections DragonflyHallReverb DragonflyPlateReverb DragonflyRoomReverb ; do cp bin/$i /usr/local/bin ; done
for i in DragonflyEarlyReflections DragonflyHallReverb DragonflyPlateReverb DragonflyRoomReverb ; do cp bin/$i-vst.so /usr/local/lib/lxvst ; done
for i in DragonflyEarlyReflections DragonflyHallReverb DragonflyPlateReverb DragonflyRoomReverb ; do cp -r bin/$i.lv2 /usr/local/lib/lv2 ; done

tar czf /tmp/dragonfly-reverb-3.0.0.armv7l.tar.gz /usr/local/bin/Dragonfly* /usr/local/lib/lxvst/Dragonfly* /usr/local/lib/lv2/Dragonfly*
tar czf /tmp/dragonfly-reverb-3.0.0.aarch64.tar.gz /usr/local/bin/Dragonfly* /usr/local/lib/lxvst/Dragonfly* /usr/local/lib/lv2/Dragonfly*
tar czf /tmp/dragonfly-reverb-3.0.0.i686.tar.gz /usr/local/bin/Dragonfly* /usr/local/lib/lxvst/Dragonfly* /usr/local/lib/lv2/Dragonfly*
tar czf /tmp/dragonfly-reverb-3.0.0.x86_64.tar.gz /usr/local/bin/Dragonfly* /usr/local/lib/lxvst/Dragonfly* /usr/local/lib/lv2/Dragonfly*
