# 🛡️ OPSEC — Comment se protéger en ligne

> **Niveau** : Débutant | **Durée** : 30 min | **Mis à jour** : 2026

---

## 📌 Table des matières

1. [C'est quoi l'OPSEC ?](#cest-quoi-lopsec)
2. [Étape 1 — Changer d'OS](#étape-1--changer-dos)
3. [Étape 2 — Protéger ton réseau](#étape-2--protéger-ton-réseau)
4. [Étape 3 — Le réseau Tor](#étape-3--le-réseau-tor)
5. [Étape 4 — VPN](#étape-4--vpn)
6. [Étape 5 — Métadonnées et mises à jour](#étape-5--métadonnées-et-mises-à-jour)
7. [Étape 6 — Mots de passe](#étape-6--mots-de-passe)
8. [Étape 7 — Anonymat maximal](#étape-7--anonymat-maximal)
9. [Résumé](#résumé)

---

## C'est quoi l'OPSEC ?

> ⚠️ **ATTENTION** — L'OPSEC protège tes informations comportementales et opérationnelles contre l'analyse humaine et technique. Il est **totalement légal** de l'utiliser pour se protéger.

**OPSEC = Operational Security** = l'art de ne pas laisser de traces.

En cybersécurité, l'OPSEC c'est l'ensemble des pratiques qui permettent de :
- Protéger ton identité réelle en ligne
- Cacher tes méthodes de travail à un adversaire
- Limiter les informations qu'un attaquant peut collecter sur toi
- Rester anonyme pendant une investigation ou un pentest

> 💡 **Règle d'or** : Si tu ne veux pas qu'une information soit trouvée, ne la publie jamais — même sous une forme que tu crois anonyme.

---

## Étape 1 — Changer d'OS

### Pourquoi Linux ?

![Linux Tux](images/Pasted_image_20260607134041.png)

La première chose à faire pour améliorer ton OPSEC, c'est de **changer de système d'exploitation**. Windows envoie énormément de données à Microsoft. Linux te donne le contrôle total de ta machine — et en plus, c'est gratuit.

> Même une grand-mère peut utiliser Linux ! Les interfaces modernes sont très simples.

### Quel Linux choisir ?

| Profil | OS recommandé | Pourquoi |
|--------|--------------|----------|
| Débutant grand public | **Debian + Cinnamon** | Simple, stable, pas d'Ubuntu |
| Étudiant en cyber | **Kali Linux** | Tous les outils préinstallés |
| PC peu puissant | **Parrot OS** | Léger et orienté sécurité |
| PC puissant + paranoïa | **Qubes OS** | Compartimentation totale par VMs |
| Fainéant 😄 | **Machine virtuelle** | VirtualBox ou VMware sur ton OS actuel |

### Installer VirtualBox (solution facile pour commencer)

```bash
# Sur Debian/Ubuntu
sudo apt update
sudo apt install virtualbox virtualbox-ext-pack

# Télécharger une image Kali Linux
# https://www.kali.org/get-kali/#kali-virtual-machines
# Importer directement le fichier .ova dans VirtualBox
```

> 💡 **Conseil** : C'est toi qui gères ton OPSEC — adapte-le à ton niveau et tes besoins.

---

## Étape 2 — Protéger ton réseau

### Pare-feu, DNS, et navigateur

Tu dois mettre en place plusieurs protections sur ton PC :

#### Activer le pare-feu sur Linux

```bash
# Installer UFW (pare-feu simple)
sudo apt install ufw

# Activer le pare-feu
sudo ufw enable

# Voir le statut
sudo ufw status verbose

# Bloquer tout trafic entrant par défaut
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

#### Changer ton DNS (éviter les écoutes de ton FAI)

```bash
# Installer et utiliser un DNS chiffré (DNS over HTTPS)
sudo apt install systemd-resolved

# Utiliser le DNS de Cloudflare ou de Quad9
# Éditer la config
sudo nano /etc/systemd/resolved.conf

# Ajouter ces lignes :
# DNS=1.1.1.1 9.9.9.9
# DNSOverTLS=yes

sudo systemctl restart systemd-resolved
```

#### Navigateur recommandé

- **Mozilla Firefox** avec les extensions suivantes :
  - `uBlock Origin` — bloque les pubs et trackers
  - `Privacy Badger` — bloque les traqueurs invisibles
  - `NoScript` — bloque les scripts non autorisés

- **Brave Browser** — alternative tout-en-un avec blocage intégré

```bash
# Installer Brave sur Debian/Ubuntu
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg \
  https://brave-keyring.s3.brave.com/brave-browser-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] \
  https://brave-keyring.s3.brave.com/ stable main" | \
  sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update && sudo apt install brave-browser
```

> 💡 Utilise **Firefox pour tes recherches du quotidien** et **Tor Browser pour l'anonymat** (voir section suivante).

---

## Étape 3 — Le réseau Tor

![Tor Browser](images/Pasted_image_20260607135252.png)

### C'est quoi Tor ?

Le réseau **Tor** (The Onion Router) est un réseau qui fait passer ta connexion par **3 pays différents** avant d'atteindre le site que tu visites. Chaque relais ne connaît que le précédent et le suivant — personne ne voit tout le chemin.

```
Toi → Relais 1 (France) → Relais 2 (Allemagne) → Relais 3 (Japon) → Site web
```

> C'est la dinguerie de passer par trois circuits ! 🔥

### Installer Tor Browser

```bash
# Méthode 1 — Via apt (Kali/Debian)
sudo apt update && sudo apt install tor torbrowser-launcher

# Lancer le navigateur Tor
torbrowser-launcher

# Méthode 2 — Téléchargement direct
# https://www.torproject.org/download/
```

### Utiliser Tor en ligne de commande

```bash
# Installer Tor
sudo apt install tor

# Démarrer le service
sudo systemctl start tor
sudo systemctl enable tor

# Vérifier que Tor tourne
sudo systemctl status tor

# Utiliser Tor avec un outil (exemple avec curl)
curl --socks5-hostname 127.0.0.1:9050 https://check.torproject.org/api/ip
```

### Renseigne-toi aussi sur I2P

**I2P** (Invisible Internet Project) est une alternative à Tor, encore plus anonyme pour les communications internes. À explorer quand tu maîtrises Tor.

```bash
# Installer I2P
sudo apt install i2p

# Lancer I2P
i2prouter start
# Interface accessible sur : http://127.0.0.1:7657
```

> ⚠️ **Tor ne suffit pas seul** — combine-le avec les autres protections de ce guide.

---

## Étape 4 — VPN

![Mullvad VPN](images/Pasted_image_20260607135909.png)

### VPN : attention aux arnaques !

> ⚠️ **IMPORTANT** : Un VPN, c'est donner ta confiance à une autre entreprise. Tu déplaces le problème, tu ne le supprimes pas. Choisis un VPN **sans logs** et **audité indépendamment**.

### VPN recommandés

| VPN | Prix | Avantages |
|-----|------|-----------|
| **Mullvad** | 5€/mois | Sans compte email, accepte cash et crypto, audité |
| **ProtonVPN** | Gratuit / Payant | Open source, basé en Suisse, version gratuite disponible |

### Installer ProtonVPN (gratuit)

```bash
# Télécharger ProtonVPN sur Debian/Ubuntu
wget https://repo.protonvpn.com/debian/dists/stable/main/binary-all/protonvpn-stable-release_1.0.3-3_all.deb
sudo dpkg -i protonvpn-stable-release_1.0.3-3_all.deb
sudo apt update && sudo apt install proton-vpn-gnome-desktop

# Lancer ProtonVPN
protonvpn-app
```

### Installer Mullvad VPN

```bash
# Ajouter le dépôt Mullvad
sudo curl -fsSLo /usr/share/keyrings/mullvad-keyring.asc \
  https://repository.mullvad.net/deb/mullvad-keyring.asc

echo "deb [signed-by=/usr/share/keyrings/mullvad-keyring.asc arch=amd64] \
  https://repository.mullvad.net/deb/stable stable main" | \
  sudo tee /etc/apt/sources.list.d/mullvad.list

sudo apt update && sudo apt install mullvad-vpn

# Lancer Mullvad
mullvad-vpn
```

### Numéro de téléphone jetable

Pour les inscriptions en ligne qui demandent un numéro, utilise des services de numéros temporaires :
- **MySudo** — numéros jetables
- **JMP.chat** — numéro XMPP anonyme
- **SMS-Activate** — numéros temporaires

---

## Étape 5 — Métadonnées et mises à jour

### Nettoyer les métadonnées de tes fichiers

Les photos, documents Word, PDF contiennent des **métadonnées cachées** : ton nom, ton logiciel, ta localisation GPS, la date et l'heure exacte...

```bash
# Installer ExifTool
sudo apt install libimage-exiftool-perl

# Voir toutes les métadonnées d'une image
exiftool photo.jpg

# Supprimer TOUTES les métadonnées
exiftool -all= photo.jpg

# Supprimer les métadonnées de tous les fichiers d'un dossier
exiftool -all= /chemin/dossier/

# Installer MAT2 (nettoyage automatique)
sudo apt install mat2

# Nettoyer un fichier avec MAT2
mat2 document.pdf
mat2 photo.jpg
```

### Mettre à jour ses systèmes régulièrement

```bash
# Mettre à jour Kali/Debian
sudo apt update && sudo apt upgrade -y

# Vérifier les mises à jour de sécurité
sudo apt list --upgradable

# Mettre à jour automatiquement les correctifs de sécurité
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

### Sécuriser ses emails

- Utilise **ProtonMail** ou **Tutanota** — chiffrés de bout en bout
- Crée des alias avec **SimpleLogin** pour ne jamais donner ta vraie adresse

```bash
# Installer un client mail sécurisé
sudo apt install thunderbird
# Ajouter l'extension Enigmail pour le chiffrement GPG
```

---

## Étape 6 — Mots de passe

### Utiliser un gestionnaire de mots de passe

Un bon mot de passe = long, unique, aléatoire. **KeePass** stocke tout localement, sans cloud.

```bash
# Installer KeePassXC (version moderne de KeePass)
sudo apt install keepassxc

# Lancer KeePassXC
keepassxc
```

**Bonnes pratiques :**
- Un mot de passe **différent** pour chaque site
- Minimum **20 caractères** avec majuscules, chiffres, symboles
- Ne jamais réutiliser un mot de passe
- Activer la **double authentification (2FA)** partout

```bash
# Générer un mot de passe aléatoire en ligne de commande
openssl rand -base64 32

# Ou avec pwgen
sudo apt install pwgen
pwgen -s 32 1
```

---

## Étape 7 — Anonymat maximal

![Tor + Tails](images/Pasted_image_20260607140421.png)

![Tails OS](images/Pasted_image_20260607140552.png)

### Tails OS — Zéro trace garantie

**Tails** est un système d'exploitation live sur clé USB. Il démarre sur n'importe quel PC, fait passer tout le trafic par Tor, et **efface tout** à l'extinction. Zéro trace sur la machine.

```
Clé USB Tails → Démarrage → Travail anonyme → Extinction → Zéro trace ✅
```

**Télécharger et installer Tails :**
1. Va sur **tails.boum.org**
2. Télécharge l'image ISO
3. Grave-la sur une clé USB de 8 Go minimum

```bash
# Graver Tails sur une clé USB depuis Linux
# Remplace /dev/sdX par ta clé USB (vérifie avec lsblk)
sudo dd if=tails-amd64-6.x.img of=/dev/sdX bs=16M oflag=direct status=progress
```

> ⚠️ **ATTENTION** : Vérifie bien le nom de ta clé USB avant de lancer cette commande !

### Machines virtuelles pour les enquêtes

Pour tes investigations OSINT, utilise **une VM dédiée par mission** :

```bash
# Installer VirtualBox
sudo apt install virtualbox

# Créer un snapshot avant chaque mission
# → Si quelque chose tourne mal, tu reviens à l'état initial

# Installer Vagrant pour automatiser les VMs
sudo apt install vagrant
```

**Workflow professionnel OSINT :**
```
1. Snapshot de la VM propre
2. Lancer la VM + VPN + Tor
3. Faire l'investigation
4. Exporter les résultats
5. Revenir au snapshot propre → zéro trace
```

---

## Résumé

| Étape | Action | Outil |
|-------|--------|-------|
| 1 | Changer d'OS | Debian, Kali, Parrot, Qubes |
| 2 | Protéger le réseau | UFW, DNS chiffré, Firefox + uBlock |
| 3 | Anonymiser le trafic | Tor Browser, I2P |
| 4 | Masquer l'IP | Mullvad VPN, ProtonVPN |
| 5 | Nettoyer les métadonnées | ExifTool, MAT2 |
| 6 | Sécuriser les mots de passe | KeePassXC |
| 7 | Anonymat maximal | Tails OS, VMs isolées |

> 🎯 **C'est toi qui gères ton OPSEC** — commence par les bases et monte en niveau progressivement. L'OPSEC parfait n'existe pas, mais chaque couche de protection compte.

---

## ⚠️ Avertissement légal

Ce tutoriel est publié à but **éducatif uniquement**. Toutes les techniques présentées sont légales dans le cadre d'une utilisation personnelle pour protéger sa vie privée. N'utilise jamais ces outils pour des activités illégales.

---

*Tutoriel rédigé par un étudiant en cybersécurité passionné 🔐*
*N'hésite pas à laisser une ⭐ si ce tuto t'a été utile !*
