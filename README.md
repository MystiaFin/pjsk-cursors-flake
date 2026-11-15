# pjsk-cursors-flake

![31 characters](https://img.shields.io/badge/characters-31-33CCBB)
![animated and static](https://img.shields.io/badge/cursors-animated_%2B_static-33CCBB)

Official Project SEKAI cursors from [colorfulstage.com](https://colorfulstage.com/media/download/), converted to Xcursor themes for Linux.

The cursors are fetched straight from SEGA's site at build time and are not redistributed here.

## Home Manager

```nix
# flake.nix
inputs.pjsk-cursors = {
  url = "github:MystiaFin/pjsk-cursors";
  inputs.nixpkgs.follows = "nixpkgs";
};

# home configuration
imports = [ inputs.pjsk-cursors.homeManagerModules.default ];

pjsk-cursor = {
  enable = true;
  character = "hatsune-miku-virtual-singer";
  animated = true; # default
  size = 32;       # default
};
```

This sets `home.pointerCursor`, so remove any other `home.pointerCursor` definition.

## NixOS without Home Manager

Add the same flake input, then install the theme system-wide:

```nix
# configuration.nix
environment.systemPackages = [
  inputs.pjsk-cursors.packages.${pkgs.stdenv.hostPlatform.system}.hatsune-miku-virtual-singer-animated
];

environment.variables = {
  XCURSOR_THEME = "pjsk-hatsune-miku-virtual-singer-animated";
  XCURSOR_SIZE = "32";
};
```

Some desktops (GNOME, KDE) ignore `XCURSOR_THEME`; pick the theme in their cursor settings instead.

## Other distros

Any distro with [Nix](https://nixos.org/download/) installed can build a theme and copy it into your icons folder:

```sh
nix build github:MystiaFin/pjsk-cursors#hatsune-miku-virtual-singer-animated
mkdir -p ~/.local/share/icons
cp -r --no-preserve=mode result/share/icons/pjsk-hatsune-miku-virtual-singer-animated ~/.local/share/icons/
```

Then pick `pjsk-hatsune-miku-virtual-singer-animated` in your desktop's cursor settings, or set it directly, for example:

```sh
gsettings set org.gnome.desktop.interface cursor-theme pjsk-hatsune-miku-virtual-singer-animated  # GNOME
hyprctl setcursor pjsk-hatsune-miku-virtual-singer-animated 32                                    # Hyprland
```

The package is `<name>-animated` or `<name>-static`, and its theme is the same with a `pjsk-` prefix.
Building the default package (`nix build github:MystiaFin/pjsk-cursors`) gives you every theme at once.

## Characters

Previews are SEGA's own images from colorfulstage.com.

| Group | Preview | Name |
| --- | --- | --- |
| VIRTUAL SINGER | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Miku%20VS.png" width="120"> | `hatsune-miku-virtual-singer` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Rin.png" width="120"> | `kagamine-rin` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Len.png" width="120"> | `kagamine-len` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Luka.png" width="120"> | `megurine-luka` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_MEIKO.png" width="120"> | `meiko` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_KAITO.png" width="120"> | `kaito` |
| Leo/need | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Miku%20LN.png" width="120"> | `hatsune-miku-leo-need` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Ichika.png" width="120"> | `hoshino-ichika` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Saki.png" width="120"> | `tenma-saki` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Honami.png" width="120"> | `mochizuki-honami` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Shiho.png" width="120"> | `hinomori-shiho` |
| MORE MORE JUMP! | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Miku%20MMJ.png" width="120"> | `hatsune-miku-more-more-jump` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Minori.png" width="120"> | `hanasato-minori` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Haruka.png" width="120"> | `kiritani-haruka` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Airi.png" width="120"> | `momoi-airi` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Shizuku.png" width="120"> | `hinomori-shizuku` |
| Vivid BAD SQUAD | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Miku%20VBS.png" width="120"> | `hatsune-miku-vivid-bad-squad` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Kohane.png" width="120"> | `azusawa-kohane` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_An.png" width="120"> | `shiraishi-an` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Akito.png" width="120"> | `shinonome-akito` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Toya.png" width="120"> | `aoyagi-toya` |
| Wonderlands×Showtime | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Miku%20WxS.png" width="120"> | `hatsune-miku-wonderlands-x-showtime` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Tsukasa.png" width="120"> | `tenma-tsukasa` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Emu.png" width="120"> | `otori-emu` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Nene.png" width="120"> | `kusanagi-nene` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Rui.png" width="120"> | `kamishiro-rui` |
| 25-ji, Nightcord de. | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Miku%20N25.png" width="120"> | `hatsune-miku-nightcord-at-25` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Kanade.png" width="120"> | `yoisaki-kanade` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Mafuyu.png" width="120"> | `asahina-mafuyu` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Ena.png" width="120"> | `shinonome-ena` |
|  | <img src="https://colorfulstage.com/upload_images/media/Download/Website%20Cursor_Animated_Mizuki.png" width="120"> | `akiyama-mizuki` |
