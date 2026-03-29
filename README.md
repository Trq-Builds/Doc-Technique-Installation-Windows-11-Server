# ` 🪟 `︲Doc-Technique-Installation-Windows-Server-2025

<p align="center">
  <img src="https://img.shields.io/badge/Windows_Server-2025-0078D6?logo=windows&logoColor=white&style=for-the-badge">
  <img src="https://img.shields.io/badge/Type-Server_OS-0056B3?style=for-the-badge">
  <img src="https://img.shields.io/badge/Guide-Installation-007ACC?style=for-the-badge">
</p>

---

Ce dépôt GitHub met à disposition une documentation claire et complète pour réaliser une installation propre de Windows 11 Server en machine virtuelle, grâce à un guide structuré étape par étape et illustré de captures d’écran pour faciliter la compréhension.

---

## ` 📑 `︲Sommaire (cliquez pour accéder directement à la section souhaitée)

1. [` 🟦 `︲Introduction.](#introduction)
   - [` 🧰 `︲Prérequis & outils nécessaires.](#prérequis--outils-nécessaires)


---

2. [` 💾 `︲Téléchargement & Préparation des fichiers.](#téléchargement--préparation-des-fichiers)
   - [` 🌐 `︲Téléchargement officiel de l'ISO Windows Server 2025.](#téléchargement-officiel-de-liso-windows-server-2025)
   - [` 🧲 `︲Vérification de l'intégrité de l'ISO (SHA256).](#vérification-de-lintégrité-de-liso-sha256)
   - [` 🗂️ `︲Organisation des fichiers pour la VM.](#organisation-des-fichiers-pour-la-vm)


---

3. [` 🛠️ `︲Configuration de la machine virtuelle.](#configuration-de-la-machine-virtuelle)
   - [` ⚙️ `︲Paramètres matériels : RAM, CPU, Disque.](#paramètres-matériels--ram-cpu-disque)
   - [` 🧩 `︲Configuration réseau : DHCP / NAT / Bridge.](#configuration-réseau--dhcp--nat--bridge)
   - [` 📎 `︲Ajout de l'ISO dans le lecteur virtuel.](#ajout-de-liso-dans-le-lecteur-virtuel)
   - [` 🛡️ `︲Paramètres UEFI / Secure Boot / TPM virtuel.](#paramètres-uefi--secure-boot--tpm-virtuel)


---

4. [` 💿 `︲Installation de Windows Server 2025.](#installation-de-windows-server-2025)
   - [` 🌍 `︲Choix de la langue, région & clavier.](#choix-de-la-langue-région--clavier)
   - [` 🧱 `︲Partitionnement du disque virtuel.](#partitionnement-du-disque-virtuel)
   - [` 🚀 `︲Lancement de l'installation.](#lancement-de-linstallation)
   - [` 🔑 `︲Saisie de la clé produit & méthode d’installation.](#saisie-de-la-clé-produit--methode-dinstallation)

---

5. [` 👤 `︲Configuration post-installation.](#configuration-post-installation)
   - [` 👤 `︲Création du compte administrateur local.](#création-du-compte-administrateur-local)
   - [` 🔐 `︲Paramètres de sécurité et rôle serveur.](#paramètres-de-sécurité-et-rôle-serveur)
   - [` 🌐 `︲Connexion réseau & mise à jour.](#connexion-réseau--mise-à-jour)

---

6. [` ✅ `︲Conclusion & Annexes.](#conclusion-et-annexes)


---

7. [` 🧰 `︲Outils & Ressources utilisés.](#outils--ressources-utilisés)

---

<a id="introduction"></a>
## `🟦`︲Introduction

Ce guide propose une **documentation complète et progressive** pour installer Windows Server 2025 en machine virtuelle.
Il couvre **toutes les étapes**, depuis le téléchargement de l’ISO jusqu’à la configuration post-installation, avec un focus sur la **sécurité et la bonne organisation** des fichiers et ressources.

---

<a id="prérequis--outils-nécessaires"></a>
### `🧰`︲Prérequis & outils nécessaires

> [!IMPORTANT]
> Pour suivre ce guide, il est recommandé de disposer de :

* `🌐`︲**ISO Windows Server 2025** — Téléchargement officiel [`🌐`](https://www.microsoft.com/fr-fr/software-download/windowsserver)
* `📦`︲**Hyperviseur compatible VM** : VMware Workstation / Player, VirtualBox, Hyper-V, etc.
* `💻`︲**Hôte avec ressources suffisantes** : 4 Go+ RAM, 2 cœurs CPU, 80 Go disque minimum
* `☕`︲**Patience et rigueur** pour suivre chaque étape correctement

> [!NOTE]
> Ce guide est pensé pour un **déploiement en VM**. Pour une installation physique, certaines étapes (TPM, Secure Boot) devront être adaptées.

---

<a id=""></a>
### `🌐`︲Téléchargement officiel de l'ISO Windows Server 2025

---

Pour installer Windows Server 2025 en machine virtuelle, il est indispensable d’obtenir **l’ISO officiel** depuis Microsoft. Cela garantit l’intégrité, la compatibilité et l’absence de modifications non autorisées.

#### Étapes de téléchargement

1. Accéder à la page officielle de téléchargement de Windows Server :
   [`🌐 Microsoft Windows Server 2025`](https://www.microsoft.com/fr-fr/software-download/windowsserver)
2. Sélectionner l’édition souhaitée (Standard, Datacenter, Evaluation, etc.).
3. Choisir **la langue**.
4. Cliquer sur **Télécharger l’ISO**.
5. Enregistrer le fichier dans un dossier dédié pour les VM (ex : `VM-WindowsServer2025/ISO`).

> [!IMPORTANT]
>
> * Toujours vérifier que l’ISO provient de Microsoft pour éviter tout ISO corrompu ou modifié.
> * Conserver le fichier dans un emplacement facile à retrouver pour la configuration de la VM.

> [!NOTE]
>
> * Pour les tests et formations, l’édition **Evaluation** est souvent suffisante et gratuite pour 180 jours.
> * Les ISO officielles incluent toutes les éditions de Windows Server et peuvent être utilisées pour plusieurs déploiements VM.

---
