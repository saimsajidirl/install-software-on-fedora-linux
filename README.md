# Install VLC
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install vlc

# Install Upscayl

sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install -y flathub org.upscayl.Upscayl

# Install Google Chrome
sudo dnf install -y fedora-workstation-repositories
sudo dnf config-manager setopt google-chrome.enabled=1
sudo dnf install -y google-chrome-stable

# Install Brave
sudo dnf install -y dnf-plugins-core
sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
sudo dnf install -y brave-browser

# Install Python
sudo dnf install -y python3 python3-pip python3-devel

# Install VS Code
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
sudo dnf check-update
sudo dnf install -y code

# Install PostgreSQL
sudo dnf install -y postgresql-server postgresql-contrib
sudo postgresql-setup --initdb --unit postgresql
sudo systemctl enable --now postgresql

# Install MongoDB & MongoDB Compass
sudo tee /etc/yum.repos.d/mongodb-org.repo > /dev/null <<'EOF'
[mongodb-org-7.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/7.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-7.0.asc
EOF
sudo dnf install -y mongodb-org
sudo systemctl enable --now mongod
flatpak install -y flathub com.mongodb.Compass
# 
