# linux_kernel_with_BCM4313_kernel_panic_fix_arch
Arch-Linux package with the default linux kernel with the patch from https://patchwork.kernel.org/project/linux-wireless/patch/20201116030635.645811-1-dima@arista.com/ to fix stability issues with that wifi module
# usage
## build 
*Note:* you can skip this step and use the packages provided, e.g. https://github.com/Tomok/linux_kernel_with_BCM4313_kernel_panic_fix_arch/releases/latest

* import gpg keys of the original maintainer so that gpg validation passes:
```bash
gpg --receive-keys 3B94A80E50A477C   
# edit that key and set it to trusted
gpg --edit-key 3B94A80E50A477C7
```
* run `makepkg -s` to build the package, this will take a while (~19h on my old laptop), as it compiles the whole kernel with all modules selected by the default arch linux
## install
* install the created packages
```bash
sudo pacman -U linux-brcmsmac-window-size-fixed-5.10.7.arch1-1-x86_64.pkg.tar.zst linux-brcmsmac-window-size-fixed-headers-5.10.7.arch1-1-x86_64.pkg.tar.zst
```
* update your bootmanager to include the new kernel
```bash
# in case of grub2 with auto configuration:
sudo grub-mkconfig -o /boot/grub/grub.cfg
```


# Credit
I am not the author of the patch, I just packaged it for my machine.
