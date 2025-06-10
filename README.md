
# 📡 WiFi Password Viewer (Windows PowerShell)

![GitHub last commit](https://img.shields.io/github/last-commit/Skykiller099/Powershell-Script-Wifi?style=for-the-badge)
![GitHub repo size](https://img.shields.io/github/repo-size/Skykiller099/Powershell-Script-Wifi?style=for-the-badge)
![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

## 🚀 À propos

Ce script PowerShell simple et direct est conçu pour vous permettre d'accéder aux mots de passe des réseaux Wi-Fi que votre système Windows a précédemment enregistrés. Il utilise les commandes natives de Windows (`netsh wlan`) pour récupérer ces informations.

## ⚠️ Avertissement de sécurité

L'utilisation de ce script implique l'accès à des informations sensibles.
* **Usage responsable :** Utilisez cet outil uniquement sur vos propres machines ou avec l'autorisation explicite et préalable du propriétaire.
* **Confidentialité :** Les mots de passe sont confidentiels. Ne partagez pas les informations récupérées avec des personnes non autorisées.
* **Responsabilité :** L'auteur décline toute responsabilité en cas d'utilisation abusive ou illégale de ce script. Vous êtes entièrement responsable de vos actions.

## 💻 Utilisation

1.  Ouvrez une console PowerShell.
2.  Copiez et collez l'intégralité du script ci-dessous directement dans la fenêtre PowerShell.
3.  Appuyez sur `Entrée` pour exécuter le script.

## 📜 Le Script

```powershell
$profiles = (netsh wlan show profiles | Select-String "All User Profile").line -replace ".*: ",""
foreach ($ssid in $profiles) {
    $password = (netsh wlan show profile name="$ssid" key clear | Select-String "Key Content").line -replace ".*: ",""
    if ($password) {
        $password = $password.line -replace ".*: ",""
    } else {
        $password = "Not Available"
    }
    Write-Output "SSID: $ssid | Password: $password"
}```

👤 Auteur
Skykiller099
 GitHub: https://github.com/Skykiller099


📄 Licence
Ce projet est distribué sous la licence MIT.
MIT License

Copyright (c) 2025 Skykiller099

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

