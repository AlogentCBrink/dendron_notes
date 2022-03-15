---
id: a6myescadpaisla44mguppw
title: Starship
desc: ''
updated: 1646329406201
created: 1646329028567
---

### Install Starship
https://starship.rs/  
```bash
sh -c "$(curl -fsSL https://starship.rs/install.sh)"
```
^inst_star
### Config Starship
#### Update .bashrc
```bash
vim .bashrc
```  
Add to the end of your .bashrc: 
```
# set an icon based on the distro
# make sure your font is compatible with https://github.com/lukas-w/font-logos
case $_distro in
    *kali*)                  ICON="ﴣ";;
    *arch*)                  ICON="";;
    *debian*)                ICON="";;
    *raspbian*)              ICON="";;
    *ubuntu*)                ICON="";;
    *elementary*)            ICON="";;
    *fedora*)                ICON="";;
    *coreos*)                ICON="";;
    *gentoo*)                ICON="";;
    *mageia*)                ICON="";;
    *centos*)                ICON="";;
    *opensuse*|*tumbleweed*) ICON="";;
    *sabayon*)               ICON="";;
    *slackware*)             ICON="";;
    *linuxmint*)             ICON="";;
    *alpine*)                ICON="";;
    *aosc*)                  ICON="";;
    *nixos*)                 ICON="";;
    *devuan*)                ICON="";;
    *manjaro*)               ICON="";;
    *rhel*)                  ICON="";;
    *macos*)                 ICON="";;
    *)                       ICON="";;
esac

export STARSHIP_DISTRO="$ICON"

# Load Starship
eval "$(starship init bash)"
```  
#### Create Starship Config:
```bash
touch ~/.config/starship.toml
sudo vim ~/.config/starship.toml
```
Insert into .toml    
```
# ~/.config/starship.toml

# Inserts a blank line between shell prompts
add_newline = true

# Change command timeout from 500 to 1000 ms
command_timeout = 1000

# Change the default prompt format
format = """\
[╭╴](238)$env_var\
$all[╰─](238)$character"""
# 
# Change the default prompt characters
[character]
success_symbol = "[](green)"
error_symbol = "[](bold red)"

# Shows an icon that should be included by zshrc script based on the distribution or os
[env_var.STARSHIP_DISTRO]
format = '[$env_value](bold white) '
variable = "STARSHIP_DISTRO"
disabled = false

# Shows the username
[username]
style_user = "white bold"
style_root = "black bold"
format = "[$user]($style) "
disabled = false
show_always = true

[directory]
truncation_length = 3
truncation_symbol = "…/"
home_symbol = " ~"
read_only_style = "197"
read_only = "  "
format = "at [$path]($style)[$read_only]($read_only_style) "

[git_branch]
symbol = " "
format = "on [$symbol$branch]($style) "
truncation_length = 4
truncation_symbol = "…/"
style = "bold green"

[git_status]
format = '[\($all_status$ahead_behind\)]($style) '
style = "bold green"
conflicted = "🏳"
up_to_date = " "
untracked = " "
ahead = "⇡${count}"
diverged = "⇕⇡${ahead_count}⇣${behind_count}"
behind = "⇣${count}"
stashed = " "
modified = " "
staged = '[++\($count\)](green)'
renamed = "襁 "
deleted = " "

[terraform]
format = "via [ terraform $version]($style) 壟 [$workspace]($style) "

[vagrant]
format = "via [ vagrant $version]($style) "

[docker_context]
format = "via [ $context](bold blue) "

[helm]
format = "via [ $version](bold purple) "

[python]
symbol = " "
python_binary = "python3"

[nodejs]
format = "via [ $version](bold green) "
disabled = true

[ruby]
format = "via [ $version]($style) "

[kubernetes]
format = 'on [ $context\($namespace\)](bold purple) '
disabled = false
[kubernetes.context_aliases]
"clcreative-k8s-staging" = "cl-k8s-staging"
"clcreative-k8s-production" = "cl-k8s-prod"

```