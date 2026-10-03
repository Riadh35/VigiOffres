# VigiOffres 4.0.0 — Installation Windows

Veille BOAMP, demandes privées importées, dossier entreprise, préparation des réponses et suivi des opportunités.

## Fichiers

- `VigiOffres_Setup_4.0.0.exe` : installateur Windows 64 bits, Python et Qt embarqués, sans droits administrateur.
- `GUIDE_UTILISATEUR.md` : guide complet en français.
- `SHA256SUMS.txt` : empreinte de l’installateur.

## Installation

Téléchargez l’installateur, vérifiez son empreinte, double-cliquez dessus et cliquez sur **Installer**. Lancez l’application depuis le Bureau ou le menu Démarrer, puis complétez l’assistant.

L’installateur n’est pas signé ; SmartScreen peut afficher un avertissement. Vérifiez sa provenance avant de poursuivre. Internet est nécessaire pour BOAMP et les flux.

## Fonctionnalités

- Recherche BOAMP avec critères géographiques, mots clés et score expliqué.
- Imports CSV / `.eml`, saisie privée et lecture des flux RSS / Atom fournis.
- Coordonnées, pièces copiées, export du dossier ZIP et préparation des brouillons.
- Échéances, statuts, historique, recherche quotidienne et notifications.
- Sauvegarde / restauration, migration V2 / V3, thèmes et aide contextuelle.

## Données et limites

Sauvegardez et fermez l’application avant une mise à jour. Les données de `Documents\VigiOffres` sont conservées lors de l’installation et de la désinstallation.

Aucune synchronisation automatique des plateformes privées. Aucun téléchargement / analyse automatique du DCE. Aucun envoi ni dépôt automatique. Les messageries web demandent l’ajout manuel des pièces.

L’empreinte et le format PE de l’installateur ont été contrôlés pour la publication. Ce contrôle ne remplace pas un essai d’installation et d’utilisation sur le poste destinataire.

## Assistance et licence

Guide : `docs/GUIDE_UTILISATEUR.md` dans le dépôt, également joint à la release.

Guardian Wall — contact@guardianwall.fr. © 2026 Riadh BEN KHALED.

Le projet conserve la licence propriétaire déclarée dans `pyproject.toml` ; sa visibilité publique ne constitue pas une licence libre.
