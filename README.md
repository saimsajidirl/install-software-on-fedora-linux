# Install VLC
sudo dnf install -y https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm && sudo dnf install -y vlc

# Install Upscayl
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo && flatpak install -y flathub org.upscayl.Upscayl

# Install Google Chrome
sudo dnf install -y fedora-workstation-repositories && sudo dnf config-manager setopt google-chrome.enabled=1 && sudo dnf install -y google-chrome-stable

# Install Brave
sudo dnf install -y dnf-plugins-core && sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo && sudo dnf install -y brave-browser
# Install Python
sudo dnf install -y python3 python3-pip python3-devel

# Install VS Code
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc ; echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo ; sudo dnf check-update ; sudo dnf install -y code

# Install PostgreSQL
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc && echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo && sudo dnf check-update ; sudo dnf install -y code

# Install MongoDB & MongoDB Compass
echo -e "[mongodb-org-7.0]\nname=MongoDB Repository\nbaseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/7.0/x86_64/\ngpgcheck=1\nenabled=1\ngpgkey=https://www.mongodb.org/static/pgp/server-7.0.asc" | sudo tee /etc/yum.repos.d/mongodb-org.repo > /dev/null && sudo dnf install -y mongodb-org && sudo systemctl enable --now mongod && flatpak install -y flathub com.mongodb.Compass

# Install Git
sudo dnf install -y git

# Install Sublime Merge
sudo rpm --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg && sudo dnf config-manager addrepo --from-repofile=https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo && sudo dnf install -y sublime-merge
