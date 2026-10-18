# Installation et lancement du Lockscreen sur Kali Linux Live USB

## 1. Objectif

Ce document explique comment installer et utiliser notre écran de verrouillage sur Kali Linux, démarré depuis une clé USB bootable.

Le programme permet de verrouiller l'ordinateur tout en gardant le bureau visible en direct. Par exemple, une vidéo peut continuer à jouer pendant le verrouillage.

Le clavier et la souris restent bloqués. Le déverrouillage nécessite le mot de passe de l'utilisateur.

## 2. Prérequis

Pour utiliser le programme, il faut :

- Une clé USB d'au moins 8 Go (16 Go recommandés).
- Un ordinateur pouvant démarrer depuis une clé USB.
- Rufus pour créer la clé USB bootable.
- Une image ISO de Kali Linux Live.
- Une connexion Internet pour télécharger les dépendances.
- Une session X11.
- Un compte utilisateur avec un mot de passe.

## 3. Création de la clé USB bootable Kali Linux

1. Télécharger [Rufus](https://rufus.ie/fr/).
2. Aller sur le site officiel de [Kali Linux](https://www.kali.org/get-kali/#kali-live).
3. Télécharger l'image ISO **Kali Linux Live**.
4. Brancher la clé USB sur l'ordinateur.
5. Ouvrir Rufus.
6. Dans « Périphérique », sélectionner la clé USB.
7. Dans « Type de démarrage », sélectionner l'image ISO de Kali Linux Live.
8. Cliquer sur « Démarrer » et confirmer l'effacement de la clé USB.
9. Attendre la fin de la création de la clé bootable.

**Attention :** toutes les données présentes sur la clé USB seront supprimées.

## 4. Démarrage de Kali Linux depuis la clé USB

1. Laisser la clé USB branchée à l'ordinateur.
2. Redémarrer l'ordinateur.
3. Ouvrir le menu de démarrage (Boot Menu), généralement avec F12, F9, Échap ou une autre touche selon l'ordinateur.
4. Sélectionner la clé USB.
5. Dans le menu Kali Linux, choisir **Live system**.
6. Attendre le démarrage de Kali Linux.

Kali Linux fonctionne directement depuis la clé USB, sans installation sur le disque dur de l'ordinateur.

En mode Live sans persistance, les fichiers et les modifications effectuées pendant la session sont perdus après le redémarrage.

## 5. Vérification de la session X11

Ouvrir un terminal dans Kali Linux et exécuter :

```bash
echo $XDG_SESSION_TYPE
```

Le résultat doit être `x11`, car le programme ne fonctionne pas sous Wayland.

## 6. Récupération du projet

Installer Git si nécessaire :

```bash
sudo apt update
sudo apt install git
```

Cloner le dépôt GitLab :

```bash
git clone URL_DU_DEPOT
```

Remplacer `URL_DU_DEPOT` par l'adresse du dépôt GitLab du projet.

Se placer dans le dossier `lockscreen` :

```bash
cd NOM_DU_DEPOT/lockscreen
```

## 7. Installation des dépendances

Donner les droits d'exécution au script :

```bash
chmod +x install_dependencies.sh
```

Lancer l'installation :

```bash
./install_dependencies.sh
```

Les dépendances sont installées pour la session Live en cours. Elles devront être réinstallées après un redémarrage si aucune persistance n'est configurée.

## 8. Lancement du programme

Donner les droits d'exécution aux scripts :

```bash
chmod +x lock.sh saver.sh
```

Lancer le verrouillage :

```bash
./lock.sh
```

Le bureau doit rester visible en direct, mais le clavier et la souris sont bloqués.

Pour déverrouiller la session, entrer le mot de passe de l'utilisateur.

**Remarque :** le fonctionnement du Lockscreen sur Kali Linux Live USB doit encore être vérifié sur un ordinateur réel.