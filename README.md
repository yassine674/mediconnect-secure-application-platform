# 🏥 MEDICONNECT

<div align="center">
  
  ![MEDICONNECT Logo](https://img.shields.io/badge/MEDICONNECT-Healthcare%20Platform-059669?style=for-the-badge&logo=heart&logoColor=white)
  
  **Plateforme de gestion de candidatures conforme RGPD pour le secteur médical**
  
  [![PHP](https://img.shields.io/badge/PHP-8.x-777BB4?style=flat-square&logo=php&logoColor=white)](https://php.net)
  [![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://mysql.com)
  [![Apache](https://img.shields.io/badge/Apache-2.4-D22128?style=flat-square&logo=apache&logoColor=white)](https://httpd.apache.org/)
  [![License](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
  [![RGPD](https://img.shields.io/badge/RGPD-Compliant-success?style=flat-square)](https://www.cnil.fr)
  
  [📖 Documentation](#-fonctionnalités) • [🚀 Installation](#-installation) • [🔒 Sécurité](#-sécurité--rgpd) • [📸 Screenshots](#-aperçu-du-projet)

</div>

---

## 📋 Table des matières

- [À propos](#-à-propos)
- [Fonctionnalités](#-fonctionnalités)
- [Architecture](#-architecture)
- [Technologies](#-technologies-utilisées)
- [Installation](#-installation)
- [Structure du projet](#-structure-du-projet)
- [Sécurité & RGPD](#-sécurité--rgpd)
- [Aperçu du projet](#-aperçu-du-projet)
- [Utilisation](#-utilisation)
- [Auteur](#-auteur)

---

## 🎯 À propos

**MEDICONNECT** est une plateforme web sécurisée de gestion de candidatures destinée au secteur médical. Développée dans le cadre d'un projet académique axé sur la **conformité RGPD**, elle permet aux professionnels de santé de postuler en ligne tout en garantissant la protection maximale de leurs données personnelles.

### 🌟 Points forts

- ✅ **100% Conforme RGPD** - Respect strict du règlement européen
- 🔐 **Sécurité renforcée** - Authentification, hashage, sessions sécurisées
- 👥 **Gestion des rôles** - Admin, RH et visiteurs avec permissions distinctes
- 📊 **Tableaux de bord** - Interface intuitive pour gérer les candidatures
- 💾 **Sauvegarde automatique** - Integration Nextcloud pour la redondance
- 📱 **Responsive Design** - Compatible desktop, tablette et mobile

---

## ⚡ Fonctionnalités

### Pour les Candidats (Visiteurs)

- 📝 Formulaire de candidature moderne et intuitif
- 📎 Upload de CV (PDF, DOC, DOCX)
- ✉️ Confirmation de soumission avec numéro de candidature
- 🔒 Données chiffrées et sécurisées

### Pour les RH (Lecture seule)

- 👀 Consultation de toutes les candidatures
- 📥 Téléchargement des CV
- 📊 Statistiques en temps réel
- 🔍 Visualisation des détails complets

### Pour les Administrateurs (Gestion complète)

- ✏️ Modification du statut des candidatures
- 🗑️ Suppression de candidatures
- 👥 Gestion des comptes utilisateurs
- 📈 Tableaux de bord avec analytics
- 📜 Logs d'activité complets

### Sécurité & Conformité

- 🔐 Authentification sécurisée (sessions PHP)
- 🔑 Mots de passe hashés (bcrypt)
- 🛡️ Protection contre les injections SQL
- 📋 Logs de traçabilité (RGPD)
- 💾 Sauvegardes automatiques (Nextcloud)

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                    VISITEUR                         │
│     Formulaire → Submit-candidature.php             │
│              ↓                                      │
│         Base de données MySQL                       │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│              ADMIN / RH                             │
│     Login → verify-login.php → Session              │
│              ↓                                      │
│     Dashboard (Admin ou RH selon le rôle)           │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│           GESTION & SAUVEGARDES                     │
│     • Consultation candidatures                     │
│     • Téléchargement CV                             │
│     • Logs d'activité                               │
│     • Backup Nextcloud                              │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ Technologies utilisées

### Backend
- **PHP 8.x** - Langage serveur
- **MySQL/MariaDB** - Base de données relationnelle
- **Apache 2.4** - Serveur web

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling moderne avec gradients
- **JavaScript (Vanilla)** - Interactions dynamiques
- **Font Awesome** - Icons
- **Google Fonts** - Typographie (Inter)

### Sécurité
- **Password Hashing** - bcrypt (PHP password_hash)
- **Prepared Statements** - Protection injection SQL
- **Sessions PHP** - Gestion authentification
- **File Upload Validation** - Contrôle extensions et taille

### Intégrations
- **Nextcloud** - Sauvegarde automatique (WebDAV)
- **phpMyAdmin** - Administration base de données

---

## 🚀 Installation

### Prérequis

- Linux (Ubuntu/Debian recommandé)
- Apache 2.4+
- PHP 8.0+
- MySQL/MariaDB 10.x+
- phpMyAdmin (optionnel)

### Étape 1 : Installer LAMP

```bash
# Mettre à jour le système
sudo apt update && sudo apt upgrade -y

# Installer Apache, MySQL, PHP
sudo apt install apache2 mariadb-server php libapache2-mod-php php-mysql php-zip php-curl -y

# Démarrer les services
sudo systemctl start apache2 mariadb
sudo systemctl enable apache2 mariadb
```

### Étape 2 : Configurer MySQL

```bash
# Sécuriser MySQL
sudo mysql_secure_installation

# Se connecter à MySQL
sudo mysql -u root -p

# Créer la base de données
CREATE DATABASE mediconnect_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;
```

### Étape 3 : Importer le schéma de base

```bash
# Cloner le projet
git clone https://github.com/votre-username/mediconnect.git

# Aller dans le dossier
cd mediconnect

# Importer le schéma SQL
sudo mysql -u root -p mediconnect_db < database/schema.sql
```

### Étape 4 : Configurer l'application

```bash
# Copier les fichiers dans le dossier web
sudo cp -r * /var/www/html/

# Créer le dossier uploads
sudo mkdir -p /var/www/html/uploads/cv
sudo chmod 755 /var/www/html/uploads
sudo chown -R www-data:www-data /var/www/html/uploads

# Modifier les permissions
sudo chown -R www-data:www-data /var/www/html/
sudo chmod 644 /var/www/html/*.php
```

### Étape 5 : Configurer les identifiants

Éditez les fichiers PHP suivants et mettez vos identifiants MySQL :

```php
// Dans tous les fichiers PHP
$servername = "localhost";
$db_username = "root";
$db_password = "VOTRE_MOT_DE_PASSE";  // ⬅️ Modifier ici
$dbname = "mediconnect_db";
```

### Étape 6 : Créer les comptes admin/RH

```bash
# Générer les hash de mots de passe
php generate-hash.php

# Copier les hash et les insérer dans la base
sudo mysql -u root -p mediconnect_db
```

```sql
INSERT INTO users (username, email, password, role) VALUES
('admin', 'admin@mediconnect.fr', 'VOTRE_HASH_ADMIN', 'admin'),
('rh', 'rh@mediconnect.fr', 'VOTRE_HASH_RH', 'rh');
```

### Étape 7 : Tester

Accédez à : `http://localhost/` ou `http://votre-ip/`

**Identifiants par défaut :**
- **Admin** : `admin` / `admin123`
- **RH** : `rh` / `rh123`

⚠️ **Changez ces mots de passe en production !**

---

## 📁 Structure du projet

```
mediconnect/
├── 📄 index.html                       # Page d'accueil
├── 📄 formulaire-candidature.html      # Formulaire de candidature
├── 📄 admin-login.php                  # Page de connexion
├── 📄 admin-dashboard.php              # Dashboard administrateur
├── 📄 rh-dashboard.php                 # Dashboard RH
├── 📄 verify-login.php                 # Vérification authentification
├── 📄 submit-candidature.php           # Traitement candidatures
├── 📄 get-candidature-details.php      # API détails candidature
├── 📄 download-cv.php                  # Téléchargement CV
├── 📄 candidature-success.php          # Page de confirmation
├── 📄 logout.php                       # Déconnexion
├── 📄 backup-to-nextcloud.php          # Script sauvegarde
├── 📄 generate-hash.php                # Générateur de hash
├── 📁 uploads/
│   └── 📁 cv/                          # Stockage des CV
├── 📁 database/
│   └── 📄 schema.sql                   # Schéma de base de données
├── 📄 README.md                        # Documentation
└── 📄 LICENSE                          # Licence MIT
```

---

## 🔒 Sécurité & RGPD

### Mesures techniques implémentées

#### Authentification & Autorisation
- ✅ Mots de passe hashés avec **bcrypt** (coût 10)
- ✅ Sessions PHP sécurisées avec régénération d'ID
- ✅ Gestion des rôles (admin, RH, visiteur)
- ✅ Protection des routes sensibles

#### Protection des données
- ✅ Requêtes préparées (prepared statements)
- ✅ Validation et sanitisation des inputs
- ✅ Upload de fichiers sécurisé
- ✅ Contrôle des extensions (.pdf, .doc, .docx)
- ✅ Limite de taille (10 MB)

#### Traçabilité
- ✅ Table `activity_logs` pour tous les événements
- ✅ Enregistrement des connexions/déconnexions
- ✅ Logs des modifications et suppressions
- ✅ Stockage de l'adresse IP

#### Conformité RGPD

| Principe RGPD | Implémentation |
|---------------|----------------|
| **Minimisation des données** | Collecte uniquement des données nécessaires |
| **Sécurité** | Chiffrement, accès contrôlés, sauvegardes |
| **Transparence** | Informations claires sur le traitement |
| **Droits des personnes** | Accès, rectification, suppression possibles |
| **Limitation de la conservation** | Possibilité de suppression des candidatures |
| **Responsabilité** | Logs et traçabilité complète |

---

## 📸 Aperçu du projet

### Page d'accueil
![Page d'accueil](https://via.placeholder.com/800x400/059669/FFFFFF?text=Page+d%27accueil+MEDICONNECT)

*Interface moderne et professionnelle avec design vert médical*

### Formulaire de candidature
![Formulaire](https://via.placeholder.com/800x400/10b981/FFFFFF?text=Formulaire+de+Candidature)

*Formulaire intuitif avec upload de CV et validation en temps réel*

### Dashboard Administrateur
![Dashboard Admin](https://via.placeholder.com/800x400/047857/FFFFFF?text=Dashboard+Admin)

*Tableau de bord complet avec statistiques et gestion des candidatures*

### Dashboard RH
![Dashboard RH](https://via.placeholder.com/800x400/059669/FFFFFF?text=Dashboard+RH)

*Interface de consultation en lecture seule pour les RH*

---

## 💻 Utilisation

### Pour soumettre une candidature

1. Accédez à la page d'accueil
2. Cliquez sur "**Postuler**"
3. Remplissez le formulaire (champs obligatoires marqués *)
4. Uploadez votre CV (PDF, DOC ou DOCX)
5. Soumettez votre candidature
6. Notez votre numéro de candidature

### Pour se connecter (Admin/RH)

1. Cliquez sur "**Connexion Staff/Admin**"
2. Entrez vos identifiants
3. Accédez à votre tableau de bord

### Actions Admin

- ✏️ Changer le statut (En attente → En cours → Acceptée/Refusée)
- 👁️ Voir les détails complets
- 📥 Télécharger le CV
- 🗑️ Supprimer une candidature

### Actions RH

- 👁️ Consulter toutes les candidatures
- 📊 Voir les statistiques
- 📥 Télécharger les CV
- ❌ Pas de modification/suppression

---

## 🔄 Sauvegarde automatique

Configuration de la sauvegarde Nextcloud :

```bash
# Éditer le fichier de configuration
nano backup-to-nextcloud.php

# Modifier les identifiants Nextcloud
$nextcloud_url = "https://votre-nextcloud.com/remote.php/dav/files/username/";
$nextcloud_username = "votre_username";
$nextcloud_password = "votre_password";

# Tester la sauvegarde manuelle
php backup-to-nextcloud.php

# Automatiser avec CRON (tous les jours à 2h)
crontab -e
# Ajouter :
0 2 * * * php /var/www/html/backup-to-nextcloud.php >> /var/log/mediconnect-backup.log 2>&1
```

---

## 📊 Base de données

### Structure des tables

#### Table `users`
Stocke les comptes admin et RH

| Champ | Type | Description |
|-------|------|-------------|
| id | INT | ID unique |
| username | VARCHAR(50) | Nom d'utilisateur |
| email | VARCHAR(100) | Email |
| password | VARCHAR(255) | Hash du mot de passe |
| role | ENUM | 'admin' ou 'rh' |
| created_at | TIMESTAMP | Date de création |
| last_login | TIMESTAMP | Dernière connexion |

#### Table `candidatures`
Stocke les candidatures

| Champ | Type | Description |
|-------|------|-------------|
| id | INT | ID unique |
| prenom | VARCHAR(100) | Prénom |
| nom | VARCHAR(100) | Nom |
| email | VARCHAR(100) | Email |
| telephone | VARCHAR(20) | Téléphone |
| cv_path | VARCHAR(500) | Chemin du CV |
| statut | ENUM | Statut candidature |
| date_soumission | TIMESTAMP | Date d'envoi |

#### Table `activity_logs`
Logs de toutes les actions

| Champ | Type | Description |
|-------|------|-------------|
| id | INT | ID unique |
| user_id | INT | ID utilisateur |
| action | VARCHAR(100) | Type d'action |
| details | TEXT | Détails |
| ip_address | VARCHAR(45) | Adresse IP |
| created_at | TIMESTAMP | Date/heure |

---

## 🐛 Dépannage

### Les fichiers PHP se téléchargent au lieu de s'exécuter

```bash
# Activer le module PHP
sudo a2enmod php8.2  # Remplacez par votre version
sudo systemctl restart apache2
```

### Erreur "Access denied" MySQL

Vérifiez les identifiants dans les fichiers PHP et assurez-vous que l'utilisateur a les permissions.

### Impossible d'uploader des fichiers

```bash
# Vérifier les permissions
sudo chmod -R 755 /var/www/html/uploads/
sudo chown -R www-data:www-data /var/www/html/uploads/
```

---

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :

1. 🍴 Fork le projet
2. 🔧 Créer une branche (`git checkout -b feature/amelioration`)
3. 💾 Commit vos changements (`git commit -m 'Ajout d'une fonctionnalité'`)
4. 📤 Push vers la branche (`git push origin feature/amelioration`)
5. 🎉 Ouvrir une Pull Request

---



## 🙏 Remerciements

- Projet académique réalisé dans le cadre de la formation en cybersécurité


<div align="center">
  
  **⭐ Si ce projet vous a été utile, n'hésitez pas à lui donner une étoile ! ⭐**
  
  ![Made with Love](https://img.shields.io/badge/Made%20with-❤️-red?style=for-the-badge)
  ![RGPD Compliant](https://img.shields.io/badge/RGPD-Compliant-success?style=for-the-badge)
  
</div>
