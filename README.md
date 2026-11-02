1. Modo de arranque del live USB: ¿arrancaste Mint en modo UEFI? Ejecuta en el live y pega la salida:
 ```Bash
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS-Legacy
```

2. Estado de NVRAM y entradas actuales
```Bash
   sudo efibootmgr -v
   ls /sys/firmware/efi/efivars | head
   mount | grep efivars
```
3. Mensaje de error exacto del instalador o de `grub-install` (por ejemplo: efibootmgr: Could not prepare Boot variable: No space left on device o EFI variables are not supported).

4. Layout de discos:
```Bash
   lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT,PARTTYPE
   sudo fdisk -l | grep -E "Disk /dev|Disklabel"
```
5. Dónde está la partición EFI de Linux: ¿creaste una EFI propia (FAT32, ~512 MB) en el SSD de 250 GB, o el instalador reutilizó la EFI de Windows en el M.2?
6. Disco seleccionado en “Dispositivo donde instalar el cargador de arranque”: ¿/dev/sdX (SSD) o /dev/nvme0n1 (M.2)?
7. Ajustes de BIOS: ¿Secure Boot activado o desactivado? ¿CSM habilitado? ¿Fast Boot activado?
8. Síntoma actual: ¿al reiniciar el equipo arranca directo a Windows, o muestra “no bootable device”? ¿Aparece “ubuntu”/”linuxmint” en el menú de arranque de la BIOS (F8)?
