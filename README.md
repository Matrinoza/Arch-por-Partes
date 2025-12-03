# 🚀 Arch Linux por Partes — Proyecto de Configuración Total  
Un recorrido completo y documentado de cómo convertir una notebook común en una máquina afilada, minimalista y ultra-optimizada con **Arch Linux**, dual-boot con Windows y entorno limpio estilo pro.

---

## 🏷️ Badges

![Arch Linux](https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white)
![Windows 11](https://img.shields.io/badge/Windows_11-0078D4?style=for-the-badge&logo=windows&logoColor=white)
![KDE Plasma](https://img.shields.io/badge/KDE_Plasma-1D99F3?style=for-the-badge&logo=kde&logoColor=white)
![Git](https://img.shields.io/badge/GIT-black?style=for-the-badge&logo=git)
![Terminal](https://img.shields.io/badge/Terminal-Pro?style=for-the-badge)

---

## 📚 Tabla de Contenidos

- [📦 Objetivo del Proyecto](#-objetivo-del-proyecto)
- [🧩 Hardware del Equipo](#-hardware-del-equipo)
- [🪓 Particiones del Sistema](#-particiones-del-sistema)
- [🐧 Instalación de Arch Linux](#-instalación-de-arch-linux)
- [💠 KDE Plasma Minimal](#-kde-plasma-minimal)
- [🧼 Windows 11 LTSB Ultra Limpio](#-windows-11-ltsb-ultra-limpio)
- [🔁 Intercambio de Arch ↔ Windows](#-intercambio-de-arch--windows)
- [🎨 Screenshots](#-screenshots)
- [📦 Lista de Paquetes Exportada](#-lista-de-paquetes-exportada)
- [🗂️ Dotfiles y Configs](#️-dotfiles-y-configs)
- [🕒 Timeline del Proyecto](#-timeline-del-proyecto)
- [⭐ Créditos](#-créditos)

---

## 📦 Objetivo del Proyecto
Documentar paso a paso la construcción de un sistema compartido:
- 🐧 Arch Linux minimalista como **entorno principal**
- 🪟 Windows 11 LTSB reducido solo para Visual Studio
- 🌱 Optimización total de recursos
- 🔁 Compatibilidad de archivos entre ambos sistemas
- ⚙️ Configuración de terminal estilo Linux dentro de Windows
- 🌐 Proyecto expandible a Bedrock, Hyprland o NixOS en el futuro

---

## 🧩 Hardware del Equipo
- 💻 **HP Notebook — Intel i3-6006U**
- 🔧 **RAM:** 16GB DDR4 2100MHz 
- 💽 **SSD 2TB**
- 🎮 **Intel HD Graphics 520**
- 🧊 Dual-boot con UEFI

---

## 🪓 Particiones del Sistema

| Partición | Tamaño | Tipo | Uso |
|----------|--------|------|-----|
| `sda1` | 100MB | FAT32 | EFI (Windows) |
| `sda2-4` | 300GB | NTFS | Windows |
| `sda5` | 1GB | FAT32 | `/boot` |
| `sda6` | 400GB | ext4 | Arch Linux `/` |
| `sda7` | resto | NTFS | Datos compartidos |

---

## 🐧 Instalación de Arch Linux

### Comandos base

Bash
```bash
pacman -Syu
pacman -S base-devel linux linux-firmware grub efibootmgr networkmanager git vim
systemctl enable NetworkManager
```

---

Grub
```bash
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=Arch
grub-mkconfig -o /boot/grub/grub.cfg
```

---

Usuarios
```bash
useradd -m tincho
passwd xxxx
usermod -aG wheel tincho
EDITOR=vim visudo
```
---

## 💠 KDE Plasma Minimal

```bash
pacman -S plasma-meta sddm dolphin konsole ark spectacle kde-systemsettings
systemctl enable sddm
```

Extra livianos
```bash
pacman -S fastfetch fzf htop btop git vim
```

## 🧼 Windows 11 LTSB Ultra Limpio

### ✔ Apps removidas

- Edge
- Cortana
- Widgets
- OneDrive
- Xbox
- Telemetría

### ✔ Terminal estilo Linux
- Git Bash
- PowerShell con Oh-My-Posh
- Vim
- Ripgrep
- Vim (opcional)

## 🔁 Intercambio de Arch ↔ Windows

### Ambos sistemas comparten:

- Partición NTFS /mnt/datos
- Vaults de Obsidian sincronizados
- Archivos de proyectos

### Montaje automático:
`/etc/fstab`

```fstab
UUID=3D9DBF203D33F186 /mnt/datos ntfs-3g defaults,windows_names 0 0
```

## 🎨 Screenshots

### Linux terminal
<img width="803" height="442" alt="imagen" src="https://github.com/user-attachments/assets/818df23c-6437-4243-9e69-deb30f94ebdd" />

### Arch

<img width="1366" height="768" alt="imagen" src="https://github.com/user-attachments/assets/2d8992ca-622c-43fc-b620-5a7a9b03d8e4" />

### Windows Terminal

<img width="1232" height="685" alt="{1609D8E0-C785-4F1B-BCFE-FBA05F0EE35F}" src="https://github.com/user-attachments/assets/ce3e19f9-b378-4ad3-bc37-84f5862ea26b" />


### Windows

<img width="1366" height="768" alt="{BC0E2C95-F0D1-4012-9B44-9519A8FF54A4}" src="https://github.com/user-attachments/assets/12a4bef1-8173-4eb8-975c-d3a44c0b001c" />

---

<img width="882" height="585" alt="image" src="https://github.com/user-attachments/assets/a2adb767-f11a-4d9b-87cb-ed1c5b9e6fc9" />


---
Los fondos de pantalla son sacados del disco compartido asi solo tenia que tener una solo carpeta con los fondos que me gustaran e ir cambiando entre ellos

### 📦 Lista de Paquetes Exportada

```bash
pacman -Qqe > paquetes.txt
```

## 🗂️ Dotfiles y Configs
- .bashrc
- .zshrc
- .config/konsole/…
- .config/plasma-org.kde.plasma.desktop-appletsrc
- Configs de Vim/Neovim
- Montaje NTFS

## 🕒 Timeline del Proyecto

| Fecha | Cambio                                        |
| ----- | --------------------------------------------- |
| Día 1 | Instalación Windows 11 LTSB minimal           |
| Día 2 | Instalación Arch + KDE minimal                |
| Día 3 | Partición NTFS compartida                     |
| Día 4 | Setup de Obsidian entre sistemas              |
| Día 5 | Terminal de Windows estilo Linux              |
| Día 6 | Repo GitHub del proyecto                      |
| Día X | *(lo que venga… Hyprland, Bedrock, Servirs…)* |

---

## ⭐ Créditos

- Configurado, roto, revivido y optimizado por Mi
- Documentado con visión a futuro y mejoras
