# initramfs image maker
simple script to make initramfs image using busybox.

# Build Linux image

## Get source
* `git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git`

## Build linux
* Making the default config
 * Duplicating your current config
  * `cp /boot/config-`uname -r`* .config`
  * `make menuconfig`: make `.config` meet to upstream

 * or make a default config, which may not have the options you are currently using. Run
 * ```make defconfig```

* Changing your config
 * If you need to make any changes to your configuration, you can run
 * ```make menuconfig```

* Building the kernel. It takes 1~2 min from scratch.
 * ```make -j80```
 * ```make -j80 modules```
 * ```make bzImage```

# Create initramfs
* run `> initramfs_make`
* you will get `initramfs.igz`

# Test
* run `kvm -kernel arch/x86/boot/bzImage -initrd <this project folder>/initramfs.igz`

# Reference
* [Howto create an initramfs image](http://jootamam.net/howto-initramfs-image.htm)
