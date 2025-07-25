## GNOME
<p>
  I used Ubuntu 22.02 (Jammy Jellyfish) for a few years and had nothing but a great experience using it. But I wanted to switch to an operating system that used less storage space. After using Arch, things have been faster, snappier and just overall a better experience personally. After the installation process, I downloaded some GNOME extensions that I used in my previous configuration.
</p>

<b>Updating Arch</b>
```
sudo pacman -Syyu
```

<b>Install Yay</b>
```
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

## Changing Terminal
<p>
  Since Arch only comes with Console by default, I decided to use GNOME terminal as my primary terminal.
</p>

<b>Installing GNOME Terminal</b>
```
sudo pacman -S gnome-terminal
```

<b>Installing the GNOME Terminal Transparency</b>
<p>
  If GNOME terminal is installed, it doesn't come installed with the transparency option. I installed it for a more custom experience.
</p>

```
yay -S gnome-terminal-transparency
```

<p>
  Once it asked to replace the current configuration of the GNOME terminal, I selected Y for YES.
</p>

## Customized My Terminal
<p>
  I decided to customize my terminal further by adding Oh-Mhy-Zsh.
</p>

<b>Installing Zsh</b>
```
sudo pacman -S zsh
```

<b>Setting Zsh as the default shell</b>
```
chsh -s $(which zsh)
```

<b>Installing Oh-My-Zsh</b>
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

<b>Installing Zsh Syntax Highlighting Plugin</b>
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

<b>Downloading and Installing Nerd Fonts</b>
<p>
  https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraMono
</p>

<b>Installing PowerLevel10k</b>
```
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

<p>
  Credit for the guide of installing Zsh and PowerLevel10k goes to @novaspirit! Here is the guide: https://github.com/novaspirit/pimpyourterm
</p>
