# HyprV4
Bu, Hyprland kurulum betiğinin V4'üdür

Hyprland için basit bir kurulum betiğiyle birlikte bir nokta yapılandırma dosyaları koleksiyonu içerir.
ÖNEMLİ - Bu betik, fiziksel donanımda temiz ve yeni bir Arch kurulumunda çalışmak üzere tasarlanmıştır

Aşağıda listelenen komutla yapılandırma dosyalarını alabilir ve paketleri elle kurabilirsiniz

Bunu SADECE Nvidia desteğine ihtiyacınız varsa yapın (önce bunu yapın)
```
yay -S linux-headers nvidia-dkms qt5-wayland qt5ct libva libva-nvidia-driver-git

```
/etc/mkinitcpio.conf düzeneyelim
```
MODULES=(nvidia nvidia_modeset nvidia_uvm nvidia_drm)
```
yeni bir initramfs görüntüsü oluştur
```
sudo mkinitcpio --config /etc/mkinitcpio.conf --generate /boot/initramfs-custom.img
```
NVIDIA Yapılandırması Oluştur
```
echo "options nvidia-drm modeset=1" | sudo tee /etc/modprobe.d/nvidia.conf
```
Doğrula
```
cat /etc/modprobe.d/nvidia.conf
```
shoud return: 
```
options nvidia-drm modeset=1
```
şimdi yeniden başlatın
```
reboot
```

Şimdi Hyprland için aşağıdakileri yükleyin

```
yay -S hyprland kitty jq mako waybar-hyprland swww swaylock-effects \
wofi wlogout xdg-desktop-portal-hyprland swappy grim slurp thunar \
polkit-gnome python-requests pamixer pavucontrol brightnessctl bluez \
bluez-utils blueman network-manager-applet gvfs thunar-archive-plugin \
file-roller btop pacman-contrib starship ttf-jetbrains-mono-nerd \
noto-fonts-emoji lxappearance xfce4-settings sddm-git sddm-sugar-candy-git 
```

Veya ekteki "set-hypr" scriptini kullanarak her şeyi kendiniz kurabilirsiniz.
(Bu fork'da "nwg-look-bin install had failed" hatasını çözülmüştür)
