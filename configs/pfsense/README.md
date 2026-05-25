# Guide : IMPORTER une configuration pfSense (fichiers XML)

Ce dépôt contient des fichiers de configuration XML pour pfSense (ex : `config-pfSense-efrei.local-.xml`).  
Suivez ces étapes pour importer correctement la configuration dans votre pfSense.

---

## Étapes pour importer un fichier XML dans pfSense

1️) **Accéder à l'interface web de pfSense**

- Ouvrez un navigateur sur votre machine ou VM.
- Allez sur : `https://<IP_LAN_PFSENSE>` (par exemple : `https://192.168.1.1`).
- Connectez-vous avec vos identifiants (`admin` / votre mot de passe).

---

2️) **Aller dans le menu de restauration**

- Allez dans :  
  `Diagnostics > Backup & Restore`

---

3️) **Sélectionner le type de configuration à restaurer**

- Dans l’onglet **Restore**, choisissez :
  - `All` si vous restaurez une configuration complète (attention : cela écrase toute la config actuelle).
  - `Firewall Rules` pour importer un fichier de règles du firewall.
  - etc.

---

4️) **Importer le fichier XML**

- Cliquez sur **Parcourir** et sélectionnez le fichier XML fourni (ex : `config-pfSense-efrei.local-.xml`).
- Cliquez sur **Restore configuration**.
- Confirmez si nécessaire.

⚠ **Attention :**
Importer un fichier complet (`config_full.xml`) remplace toute la configuration actuelle de votre pfSense (interfaces, VPN, utilisateurs, etc.).

---

5️) **Redémarrage**

- pfSense redémarre automatiquement après l'importation d'une configuration complète.
- Pour les règles ou NAT seules, cela s’applique immédiatement.

---

## Bonnes pratiques

- **Vérifiez les noms des interfaces** avant import (ex : `em0`, `em1`) pour éviter les erreurs réseau.
- **Ne publiez jamais un fichier XML complet contenant des données sensibles sur un dépôt public**.
- **Gardez une copie de votre config actuelle avant importation** via `Diagnostics > Backup & Restore > Download configuration as XML`.

---

## Fichiers fournis dans ce dépôt

- `config_full.xml` : première configuration complète

---

## Collaboration

Si vous modifiez les règles ou la config :
- Exporte ta config mise à jour.
- Anonymise les IP sensibles ou les secrets.
- Propose un commit/pull request avec un fichier descriptif (`CHANGES.md`).

----------------------------------------------------------------------------------------------------------------------------------------------------------

# Guide : EXPORTER une configuration pfSense (fichiers XML)
Ce guide décrit comment exporter des fichiers de configuration depuis pfSense pour les partager sur ce dépôt GitHub.  

---

## Étapes pour exporter un fichier XML

1️) **Accéder à l'interface web de pfSense**

- Ouvrez un navigateur.
- Connectez-vous sur l'interface :  
  `https://<IP_LAN_PFSENSE>` (ex : `https://192.168.1.1`)
- Identifiants : `admin` / votre mot de passe

---

2️) **Aller dans le menu de sauvegarde**

- Allez dans :  
  `Diagnostics > Backup & Restore`

---

3️) **Sélectionner ce que vous souhaitez exporter**

- Dans la section **Backup Area**, choisissez :
  - `All` : pour exporter toute la configuration pfSense  
  ⚠ Attention : ce fichier contiendra tout (interfaces, règles, VPN, mots de passe chiffrés...)  
  - `Firewall Rules` : uniquement les règles du pare-feu
  - `NAT` : uniquement les règles NAT
  - Autres choix : DHCP, VPN, etc.

---

4️) **Télécharger le fichier**

- Cliquez sur **Download configuration as XML**
- Le fichier sera téléchargé (ex : `config-...xml`, `pfsense_rules.xml`, `nat_rules.xml`)

---

## Bonnes pratiques avant de déposer sur GitHub

Renommez le fichier de manière claire :
- `pfsense_rules_siteA.xml`
- `nat_rules_siteA.xml`
- `config_full_siteA.xml`

**Anonymisez si nécessaire :**
- Éditez le fichier et supprimez toute donnée sensible (ex : IP publiques, secrets, pré-shared key...)

Déposez sur GitHub uniquement :
- Des fichiers utiles à l'équipe
- Des fichiers sans données confidentielles si le dépôt est public

