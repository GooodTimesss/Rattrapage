# pfSense VPN Accès Distant - Export de configuration

## Contenu
- `openvpn_config.xml` : configuration OpenVPN
- `system_config_certs.xml` : CA + certificats utilisés par le VPN

## Import
1️) Allez dans `Diagnostics > Backup & Restore > Restore`  
2️) Sélectionnez le fichier et importez :  
- `system_config_certs.xml` : restaurer les certificats + CA  
- `openvpn_config.xml` : restaurer la config OpenVPN  

Attention : L'import du `System` remplace toute la section System du pfSense (CA, certificats, users...)

## Recommandations
- Ne pas utiliser sur un pfSense déjà en production sans test préalable
- Protégez ces fichiers (contiennent des données sensibles)

----------------------------------------------------------------------------------------------
# OpenVPN accès distant - Client Config (Pour tester)

## Utilisation
1️) Téléchargez le fichier : `uservpn_Windows_Linux_Mac.ovpn`  
2) Importez-le dans votre client OpenVPN (OpenVPN Connect, Viscosity, Tunnelblick…) ou dans les paramètres réseaux de votre machine
3️) Connectez-vous en un clic (login : PDG ; mdp : 123456789)

## Attention
- Ce fichier contient les certificats, clés et paramètres pour accéder au VPN distant
- En cas de fuite, changer immédiatement les certificats et la configuration serveur
