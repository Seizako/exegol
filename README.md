# Exegol

Recueil de write-ups réalisés dans le cadre d'un module de sécurité offensive : exploitation de machines vulnérables (type CTF/TryHackMe) couvrant l'injection, le fuzzing web et le cracking.

Chaque write-up détaille la méthodologie complète : reconnaissance, énumération, exploitation, récupération du flag, failles identifiées, correctifs proposés et retour d'expérience.

## Challenges

| Write-up                                      | Difficulté | Catégorie | Résumé                                                                                                                                       |
| --------------------------------------------- | ---------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| [Batman's Secret](batman_secret.md)           | Easy       | Injection | Injection de commande via `os.system`, FTP anonyme, dossier `logs` en écriture pour exfiltrer le résultat                                    |
| [Fun With Functional](fun_with_functional.md) | Easy       | Injection | Upload de fichier Haskell compilé et exécuté côté serveur (RCE via `System.Process`)                                                         |
| [H4ck3rz](h4ck3rz.md)                         | Easy       | Fuzz      | Identifiants exposés (robots.txt + commentaire HTML), panneau shell web, sudo `NOPASSWD` mal configuré, contournement de filtre de mots-clés |
| [H4ck3rz 2](h4ck3rz_2.md)                     | Easy       | Fuzz      | Suite de H4ck3rz : reverse shell, binaire `42sh` SUID root contourné avec l'option `-p`                                                      |
| [Silence](silence.md)                         | Medium     | Fuzz      | Directory listing, archive chiffrée GPG, clé privée non protégée, identifiants dans un fichier Excel                                         |
| [Toss a Coin](toss_a_coin.md)                 | Easy       | Fuzz      | Chemin caché découvert via fuzzing récursif (ffuf), identifiants planqués dans du HTML `display: none`                                       |
| [Year 5739](year_5739.md)                     | Easy       | Injection | Port haut hors du scan par défaut, injection Python via `eval()`                                                                             |
| [Yer a Wizard](yer_a_wizard.md)               | Easy       | Cracking  | FTP anonyme, dossier caché `...`, faux mot de passe piège, triple décodage base64                                                            |

## Structure du dépôt

```
.
├── <nom_du_challenge>.md      # Write-up détaillé de chaque challenge
└── screenshots/
    └── <nom_du_challenge>/    # Captures d'écran référencées dans le write-up correspondant
```

## Méthodologie générale

La plupart des write-ups suivent le même déroulé :

1. **Reconnaissance** : scan `nmap` (ports par défaut puis tous les ports si nécessaire)
2. **Énumération** : `gobuster` / `ffuf` pour le web, `ftp`/`nc` pour les autres services
3. **Découverte** : recherche d'identifiants, de code source ou de fichiers exposés
4. **Exploitation** : injection de commande, RCE, abus de configuration (sudo, SUID), etc.
5. **Post-exploitation** : élévation de privilèges et récupération du flag
6. **Bilan** : failles trouvées, correctifs recommandés, ce qui a été appris

## Environnement

Les challenges ont été réalisés depuis [Exegol](https://exegol.com/), une plateforme de pentest sous Docker, connectée aux machines cibles via VPN.

## Outils utilisés

`nmap`, `gobuster`, `ffuf`, `curl`, `ftp`, `ssh`, `nc`, `gpg`, `libreoffice`, CyberChef.

## Avertissement

Ces write-ups documentent l'exploitation de machines volontairement vulnérables mises à disposition dans un cadre pédagogique autorisé. Les techniques décrites ne doivent pas être utilisées sur des systèmes sans autorisation explicite.
