# VigiOffres

**Repérez les opportunités. Préparez vos réponses. Suivez vos marchés.**

VigiOffres est une application Windows pour les indépendants, artisans et PME : veille des marchés publics BOAMP, centralisation des demandes privées, préparation du dossier entreprise et suivi des réponses.

**Version 4.0.0 · Windows 64 bits · Données locales · Aucun compte VigiOffres nécessaire**

## Télécharger et installer

Dans **Releases** sur ce dépôt, téléchargez **VigiOffres_Setup_4.0.0.exe**. Double-cliquez dessus, cliquez sur **Installer**, puis ouvrez VigiOffres depuis le Bureau ou le menu Démarrer.

Python et Qt sont embarqués. L’installation ne demande pas de droits administrateur et se fait dans `%LOCALAPPDATA%\Programs\VigiOffres`. Le fichier fait environ 26 Mo.

L’installateur n’est pas signé et peut déclencher SmartScreen. Vérifiez sa provenance et comparez son empreinte SHA-256 avec `SHA256SUMS.txt` joint à la release. Le guide détaille l’installation, la mise à jour et la désinstallation.

## Fonctionnalités

- Recherche BOAMP par départements, mots clés, synonymes, exclusions et période, avec score expliqué.
- Saisie des demandes privées, imports CSV et notifications `.eml`, lecture de flux RSS / Atom HTTPS fournis.
- Dossier entreprise : coordonnées, pièces copiées et export ZIP.
- Préparation de réponses et de brouillons selon le canal de la demande.
- Suivi des échéances, statuts et historique.
- Recherche BOAMP quotidienne, notifications, sauvegarde / restauration et migration V2 / V3.
- Thèmes clair et sombre, raccourcis clavier et aide contextuelle F1.

## Démarrer

1. Installez l’application et complétez l’assistant : entreprise, coordonnées, activités, départements.
2. Dans **Opportunités**, configurez la zone et les mots clés, puis cliquez sur **Rechercher sur BOAMP**.
3. Complétez **Dossier entreprise** avec les coordonnées et les pièces utiles.
4. Sélectionnez une fiche et utilisez **Répondre** pour préparer votre réponse.
5. Après l’envoi ou le dépôt réel, confirmez l’action et mettez à jour le suivi.
6. Dans **Paramètres**, créez votre première sauvegarde.

Le profil « Charpente bois — 35/22 » est un exemple modifiable. Tous les métiers et départements peuvent être configurés.

## Documentation

- [Guide complet d’utilisation](GUIDE_UTILISATEUR.md) : installation, recherche, imports, réponses, sauvegardes, migration et dépannage.
- [Notes de release 4.0.0](RELEASE_4.0.0.md).
- [Documentation technique et lancement depuis les sources](DEVELOPPEMENT.md).

## Limites à connaître

BOAMP est la seule source synchronisée automatiquement. Les plateformes privées ne sont pas interrogées automatiquement : utilisez la saisie, leurs exports autorisés, les notifications ou les flux fournis. Aucun contournement d’accès ou d’abonnement n’est effectué.

Le téléchargement et l’analyse automatiques du DCE ne sont pas disponibles. Téléchargez-le sur le profil acheteur et vérifiez les lots, pièces et échéances dans le règlement de consultation.

**Rien n’est envoyé automatiquement.** Envoyez le message ou déposez l’offre sur le service concerné, puis confirmez l’action dans VigiOffres. Outlook classique peut préparer les pièces jointes ; les messageries web demandent leur ajout manuel. Limites : 25 Mo par pièce et 20 Mo de pièces au total par brouillon.

## Données et confidentialité

Les fiches, pièces et brouillons sont conservés dans `Documents\VigiOffres`. Les recherches BOAMP, les flux et l’ouverture des services externes utilisent Internet. Aucun mot de passe de messagerie n’est demandé.

Utilisez **Paramètres → Sauvegarder maintenant**, puis copiez le ZIP sur un support externe. Mise à jour et désinstallation conservent le dossier de données. Ne publiez pas votre base, vos sauvegardes ou vos pièces clients dans ce dépôt.

## Licence et assistance

Le projet déclare une **licence propriétaire — usage interne** dans `pyproject.toml`. Un dépôt public ne constitue pas une licence libre et ne change pas cette déclaration. Les dépendances conservent leurs propres licences ; contactez l’éditeur pour les conditions de distribution et d’utilisation.

**Guardian Wall — contact@guardianwall.fr**

Pour signaler un problème, indiquez la version de l’application, la version de Windows, les étapes et le message exact. Masquez les données personnelles avant de publier une capture ou un journal.

© 2026 Riadh BEN KHALED. Anciennement MarchéPilot / Veille Bois.

