# 05 — Solución de errores comunes

Lista de errores reales encontrados:

## Error:
- La configuracion del dualboot ya que no hice bien la configuracion y no me mostraba grub
- Configuracion de la terminal ghostty (Esteticos nomas)
- Configuracion de Powershell

### Solución:
- 🟦 Comandos para el fix del dual-boot
    - Arch = /dev/sda6
    - Boot EFI de Arch = /dev/sda5
    - EFI de Windows = /dev/sda1
---

  - ✅ 1. Montar las particiones correctamente

```bash
mount /dev/sda6 /mnt
mount /dev/sda5 /mnt/boot
mount /dev/sda1 /mnt/boot/EFI
```
  - ✅ 2. Entrar al sistema

```bash
arch-chroot /mnt
```

  - ✅ 3. Instalar GRUB + EFI + os-prober

```bash
pacman -S grub efibootmgr ntfs-3g os-prober
```

  - ✅ 4. Activar búsqueda de sistemas operativos
  Editar:

```bash
nano /etc/default/grub
```

  Asegurarse de que lo siguiente este descomentado
  
```bash
GRUB_DISABLE_OS_PROBER=false
GRUB_TIMEOUT=5
GRUB_TIMEOUT_STYLE=menu
```
  Guardamos

  - ✅ 5. Instalar GRUB en UEFI

```bash
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=Arch
```

  - ✅ 6. Re-generar el grub.cfg

```bash
os-prober
grub-mkconfig -o /boot/grub/grub.cfg
```
Si os-prober detecta Windows, ya está

  - 🔥 7. Salir y reiniciar

---

- 🟥 Configuración estética de GHOSTTY

- Ghostty se maneja por: ~/.config/ghostty/config

```bash
mkdir -p ~/.config/ghostty
nano ~/.config/ghostty/config
```

En la carpeta creada

```bash
# ─── Apariencia ────────────────────────────────────────────────
font=JetBrainsMono Nerd Font
font-size=12
theme=tokyo-night-storm
background-opacity=0.90
padding=4 8
cursor-style=block
cursor-blink=true

# ─── Colores (Tokyo Night) ─────────────────────────────────────
palette=0=#1a1b26
palette=1=#f7768e
palette=2=#9ece6a
palette=3=#e0af68
palette=4=#7aa2f7
palette=5=#bb9af7
palette=6=#7dcfff
palette=7=#a9b1d6
palette=8=#414868
palette=9=#f7768e
palette=10=#9ece6a
palette=11=#e0af68
palette=12=#7aa2f7
palette=13=#bb9af7
palette=14=#7dcfff
palette=15=#c0caf5

# ─── Comportamiento ────────────────────────────────────────────
initial-window-size=100x28
confirm-close=false
scrollback-lines=50000

# ─── Keybinds útiles ───────────────────────────────────────────
keybind=Ctrl+Shift+t:new_tab
keybind=Ctrl+Shift+w:close_tab
keybind=Ctrl+Shift+Right:next_tab
keybind=Ctrl+Shift+Left:previous_tab

```
---

- 🟪 Powershell
En este caso aca no hay comando sino acciones queria instalar una version mejorada de de terminarl que es CORE de porwershell y no me dejada porque solo se puede hacer desde la tienda de microsoft y fue instalarla, descargarla y despues de eso borrar otra vez la tienda y ya quedo


---
Agregarás más con el tiempo.

