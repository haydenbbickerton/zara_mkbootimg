Modified mkbootimg for for HTC zaracl. Adjusted the ramdisk_offset to work with the zaracl.

To compile the mkbootimg yourself, place mkbootimg.c in <android-src-root>/system/core/mkbootimg/ and run:

    cd /path/to/android-src
    cd system/core/libmincrypt/
    gcc -c *.c -I../include
    ar rcs libmincrypt.a  *.o
    cd ../mkbootimg
    gcc mkbootimg.c -o mkbootimg -I../include ../libmincrypt/libmincrypt.a
    
    
    
To compile a boot.img, run this(adjust it to fit your needs):

    mkbootimg --kernel zImage --ramdisk initramfs.cpio.gz --base 0x80600000 --cmdline 'console=ttyHSL0,115200,n8 androidboot.hardware=zaracl user_debug=31' -o new_boot.img
