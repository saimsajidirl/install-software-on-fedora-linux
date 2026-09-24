# Fedora Setup Script

### Install VLC
```bash
sudo dnf install -y https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm && sudo dnf install -y vlc
```

### Install Upscayl
```bash
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo && flatpak install -y flathub org.upscayl.Upscayl
```

### Install Google Chrome
```bash
sudo dnf install -y fedora-workstation-repositories && sudo dnf config-manager setopt google-chrome.enabled=1 && sudo dnf install -y google-chrome-stable
```

### Install Brave Browser
```bash
sudo dnf install -y dnf-plugins-core && sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo && sudo dnf install -y brave-browser
```

### Install Python
```bash
sudo dnf install -y python3 python3-pip python3-devel
```

### Install VS Code
```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc && printf "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc\n" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null && sudo dnf install -y code
```

### Install PostgreSQL
```bash
sudo dnf install -y postgresql-server postgresql-contrib
```

### Install MongoDB & MongoDB Compass
```bash
printf "[mongodb-org-7.0]\nname=MongoDB Repository\nbaseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/7.0/x86_64/\ngpgcheck=1\nenabled=1\ngpgkey=https://www.mongodb.org/static/pgp/server-7.0.asc\n" | sudo tee /etc/yum.repos.d/mongodb-org.repo > /dev/null && sudo dnf install -y mongodb-org && sudo systemctl enable --now mongod && flatpak install -y flathub com.mongodb.Compass
```

### Install Git
```bash
sudo dnf install -y git
```

### Install Sublime Merge
```bash
sudo rpm --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg && sudo dnf config-manager addrepo --from-repofile=https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo && sudo dnf install -y sublime-merge
```

### Install Anti-Gravity
```bash
printf "[antigravity-rpm]\nname=Antigravity RPM Repository\nbaseurl=https://us-central1-yum.pkg.dev/projects/antigravity-auto-updater-dev/antigravity-rpm\nenabled=1\ngpgcheck=0\n" | sudo tee /etc/yum.repos.d/antigravity.repo > /dev/null && sudo dnf install -y antigravity
```

### Install Zoom
```bash
sudo dnf install -y https://zoom.us/client/latest/zoom_x86_64.rpm
```

### Install PeaZip
```bash
sudo dnf install -y peazip-qt5
```
