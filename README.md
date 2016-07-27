## Multi-boot usb

### Usage
1. Make a vfat usb disk using Gnome Disks, with label "MULTIBOOT"

2. Mount the usb disk (Example: /media/user/MULTIBOOT/)

3. copy the content of multiboot project into usb disk  
WARNING: This will remove all data on the usb disk
  ``` bash
git clone https://github.com/chenhan1218/multiboot
rsync -avP --delete multiboot/usb/ /media/user/MULTIBOOT/
  ```

4. Change value of fs_uuid in EFI/BOOT/grub.cfg and boot/grub/x86_64-efi/load.cfg from AAAA-AAAA to "uuid" of usb disk. (You can check uuid of usbdisk with `sudo blkid`)

5. Copy Debian/Ubuntu/Archlinux ISO into isos/ in usb disk. Edit the boot/grub/grub.cfg

6. Unmount the usb disk and enjoy it!.

Reference:
```
# https://wiki.archlinux.org/index.php/Multiboot_USB_drive
In case you want to boot ISOs in UEFI mode, you have to install grub for the UEFI target:

# grub-install --target x86_64-efi --efi-directory /mnt --boot-directory=/mnt/boot --removable
```

