# windows grub fuckery

fixes the dumb "error: file '/EFI/Microsoft/Boot/bootmgfw.efi' not found"

## why

for uni and work reasons, i still have to use windows for certain applications.
even though i am on IoT version of the windows, i still get updates like fuck and that,
somehow, broke the bootloader.

## how

this fix stems from [here](https://askubuntu.com/questions/1271907/dualboot-ubuntu-windows-error-file-efi-microsoft-boot-bootmgfw-efi-not-fou), i dont claim ownership of the thing.
just making it easier for me to find the fix anytime the shit is broken again.

## use

__copied straight from the stackoverflow__:


1. Download this file and save it in the Downloads folder.
2. Save your Home Path in /tmp/home.txt:
```bash
echo "$HOME" > /tmp/home.txt
```
3. Export variable HOMEOLD:
```bash
export HOMEOLD=$(cat /tmp/home.txt)
```
4. Copy .tar.gz file to EFI directory:
```bash
sudo cp $HOMEOLD/Downloads/WindowsBoot.tar.gz /boot/efi/EFI
```
5. Enter the EFI directory:
```bash
cd /boot/efi/EFI
```
6. Decompress .tar.gz file:
```bash
sudo tar -xzf WindowsBoot.tar.gz
```
7. Delete .tar.gz file:
```bash
sudo rm WindowsBoot.tar.gz
```
7. Reboot and voilà!
```bash
sudo reboot
```
