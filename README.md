# OPSEC-FR

# Méthode 1 — Via apt (Kali/Debian)
sudo apt update && sudo apt install tor torbrowser-launcher

# Lancer le navigateur Tor
torbrowser-launcher

# Méthode 2 — Téléchargement direct
# https://www.torproject.org/download/

<img width="1800" height="900" alt="Pasted image 20260607135252" src="https://github.com/user-attachments/assets/748c194f-679e-4656-8a93-1c91bff55591" />

# Télécharger ProtonVPN sur Debian/Ubuntu
wget https://repo.protonvpn.com/debian/dists/stable/main/binary-all/protonvpn-stable-release_1.0.3-3_all.deb
sudo dpkg -i protonvpn-stable-release_1.0.3-3_all.deb
sudo apt update && sudo apt install proton-vpn-gnome-desktop

# Lancer ProtonVPN
protonvpn-app
( via flatpack si sa ne marche pas) 


# Ajouter le dépôt Mullvad
sudo curl -fsSLo /usr/share/keyrings/mullvad-keyring.asc \
  https://repository.mullvad.net/deb/mullvad-keyring.asc

echo "deb [signed-by=/usr/share/keyrings/mullvad-keyring.asc arch=amd64] \
  https://repository.mullvad.net/deb/stable stable main" | \
  sudo tee /etc/apt/sources.list.d/mullvad.list

sudo apt update && sudo apt install mullvad-vpn

# Lancer Mullvad
mullvad-vpn
# Mettre à jour Kali/Debian
sudo apt update && sudo apt upgrade -y

# Vérifier les mises à jour de sécurité
sudo apt list --upgradable
<img width="1000" height="1000" alt="Pasted image 20260607135909" src="https://github.com/user-attachments/assets/3314a587-2a8b-4116-93f1-916c8a255824" />
# Mettre à jour automatiquement les correctifs de sécurité
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
<img width="1200" height="628" alt="Pasted image 20260607134041" src="https://github.com/user-attachments/assets/c01ad857-7bb9-457c-9c8b-eed7fe1d61dd" />

# Installer KeePassXC (version moderne de KeePass)
sudo apt install keepassxc

# Lancer KeePassXC
keepassxc

tails.boum.org

# Installer VirtualBox
sudo apt install virtualbox

# Créer un snapshot avant chaque mission
# → Si quelque chose tourne mal, tu reviens à l'état initial

# Installer Vagrant pour automatiser les VMs
sudo apt install vagrant

⚠️ Avertissement légal
Ce tutoriel est publié à but éducatif uniquement. Toutes les techniques présentées sont légales dans le cadre d'une utilisation personnelle pour protéger sa vie privée. N'utilise jamais ces outils pour des activités illégales.
