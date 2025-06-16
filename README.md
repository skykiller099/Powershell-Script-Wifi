9# 📡 WiFi Password Viewer (Windows PowerShell)

![GitHub last commit](https://img.shields.io/github/last-commit/Skykiller099/Powershell-Script-Wifi?style=for-the-badge)
![GitHub repo size](https://img.shields.io/github/repo-size/Skykiller099/Powershell-Script-Wifi?style=for-the-badge)
![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

---

## 🚀 Présentation

**WiFi Password Viewer** est un script PowerShell simple et efficace qui permet d’afficher les mots de passe des réseaux Wi-Fi enregistrés sur votre ordinateur Windows.  
Il utilise les commandes natives (`netsh wlan`) pour extraire les SSID et leurs mots de passe associés.

---

## 🛡️ Sécurité & Responsabilité

> **Attention :**  
> Ce script accède à des informations sensibles (mots de passe Wi-Fi).
>
> **Utilisation responsable :**  
> - Utilisez ce script uniquement sur vos propres appareils ou avec l’accord explicite du propriétaire.
> - **Ne partagez jamais les mots de passe récupérés avec des tiers non autorisés.**
> - **L’auteur décline toute responsabilité en cas d’utilisation abusive ou illégale.**

---

## 💻 Installation & Utilisation

### Prérequis

- **Windows 10 ou supérieur**
- **PowerShell** (préinstallé sur Windows)

### Étapes

1. **Ouvrez PowerShell en tant qu’administrateur**  
   *(Cliquez sur le menu Démarrer > Tapez « PowerShell » > Clic droit > Exécuter en tant qu’administrateur)*
2. **Copiez et collez le script ci-dessous dans la console PowerShell**
3. **Appuyez sur `Entrée` pour lancer le script**

---

## 📜 Script PowerShell

```
$profiles = (netsh wlan show profiles | Select-String "All User Profile").line -replace ".: ",""
foreach ($ssid in $profiles) {
$password = (netsh wlan show profile name="$ssid" key=clear | Select-String "Key Content").line -replace ".: ",""
if ($password) {
$password = $password.line -replace ".*: ",""
} else {
$password = "Not Available"
}
Write-Output "SSID: $ssid | Password: $password"
}

```



---

## ❓ FAQ

**Q : Ce script fonctionne-t-il sur toutes les versions de Windows ?**  
R : Il est compatible avec Windows 10 et versions ultérieures.

**Q : Dois-je avoir les droits administrateur ?**  
R : Oui, il est préférable d’exécuter PowerShell en tant qu’administrateur pour garantir l’accès à toutes les informations.

**Q : Les mots de passe sont-ils stockés ailleurs ?**  
R : Non, le script ne stocke rien, il affiche simplement les informations récupérées.

---

## 🤝 Contribuer

Les contributions sont les bienvenues !  
- **Signalez un bug ou proposez une amélioration** via [Issues](https://github.com/Skykiller099/Powershell-Script-Wifi/issues)
- **Proposez une Pull Request** pour ajouter des fonctionnalités ou corriger des erreurs.

---

## 👤 Auteur

**Skykiller099**  
[GitHub](https://github.com/Skykiller099)

---

## 📄 Licence

Ce projet est sous licence MIT.  

---

