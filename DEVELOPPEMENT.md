# VigiOffres

**Veillez sur les appels d'offres publics et privés. Préparez vos réponses. Suivez vos marchés.**

*Anciennement MarchéPilot / Veille Bois. « Vigi » pour la vigie qui surveille l'horizon, « Offres » pour les appels d'offres publics comme les demandes privées.*

VigiOffres est une application Windows locale pour les indépendants, artisans et PME de tous secteurs. Elle recherche les marchés publics sur le BOAMP, regroupe les demandes privées que vous importez, prépare votre dossier entreprise et vos brouillons de réponse, puis suit chaque opportunité jusqu'au résultat. Aucun compte en ligne n'est nécessaire : vos données restent sur votre ordinateur.

> Le contexte d'origine (charpente, ossature bois, bardage, terrasses, carports, garages, escaliers, pergolas en Ille-et-Vilaine et Côtes-d'Armor) est désormais un **profil d'exemple modifiable**. N'importe quel métier et n'importe quel département peuvent être configurés.

---

## 1. Installation et lancement

### Installation en un double-clic (recommandé)

Double-cliquez sur **`VigiOffres_Setup_4.0.0.exe`** et cliquez sur **Installer**. C'est tout.

- Un seul fichier d'environ 26 Mo, qui contient Python 3.13 et Qt 6.8 LTS : il n'y a rien d'autre à installer.
- Aucun droit administrateur n'est demandé. L'application est installée dans `%LOCALAPPDATA%\Programs\VigiOffres`.
- Des raccourcis sont créés sur le **Bureau** et dans le **menu Démarrer**.
- Pour désinstaller : *Paramètres Windows → Applications → Applications installées → VigiOffres → Désinstaller*. Vos données (`Documents\VigiOffres`) sont conservées.
- Pour mettre à jour, relancez simplement un installateur plus récent : l'application est remplacée et vos données restent intactes.
- Windows SmartScreen peut afficher « Windows a protégé votre ordinateur », car l'installateur n'est pas encore signé. Cliquez sur **Informations complémentaires**, puis **Exécuter quand même**. Un certificat de signature de code supprimera cet avertissement.
- Installation silencieuse (parc informatique) : `VigiOffres_Setup_4.0.0.exe /S`.

**Reconstruire l'installateur** (Linux ou WSL, avec NSIS) : `bash installer/build_installer.sh`. Le script télécharge le Python Windows officiel (empreinte SHA-256 vérifiée) et les roues PySide6, allège Qt, crée le lanceur `VigiOffres.exe` puis produit `dist/VigiOffres_Setup_<version>.exe`.


**Python compatible :** 3.10 à 3.14 (poste de référence : Windows 11 et Python 3.14.1).
**Dépendances :** `PySide6-Essentials` (6.8 LTS à 6.11) et `tzdata`. Des wheels Windows `cp310-abi3-win_amd64` sont publiés pour PySide6-Essentials 6.11.2 ; leur métadonnée annonce `Requires-Python: <3.15,>=3.10`, donc Python 3.14 est pris en charge.

### Le plus simple

Double-cliquez sur **`LANCER_VIGIOFFRES.bat`**. Au premier lancement, il crée un environnement `.venv` et installe les dépendances (connexion Internet requise), puis ouvre l'application.

### En ligne de commande (PowerShell, dans ce dossier)

```powershell
py -3 -m venv .venv
.venv\Scripts\python.exe -m pip install --upgrade pip
.venv\Scripts\python.exe -m pip install -r requirements.txt
.venv\Scripts\python.exe run_vigioffres.py
```

Pour lancer les tests :

```powershell
.venv\Scripts\python.exe -m pip install -r requirements-dev.txt
.venv\Scripts\python.exe -m pytest -q
```

Si une future version de Python n'est pas encore prise en charge par PySide6, installez Python 3.13 depuis python.org et remplacez `py -3` par `py -3.13`.

### Construire l'exécutable autonome

```powershell
powershell -ExecutionPolicy Bypass -File .\build_windows.ps1
```

Le script crée `.venv`, installe les dépendances, lance les tests puis construit `dist\VigiOffres\VigiOffres.exe` avec l'icône de l'application. **Copiez tout le dossier `dist\VigiOffres`**, pas seulement le `.exe`.

---

## 2. Parcours

1. **Premier lancement** — un assistant en 4 étapes : entreprise, coordonnées, activités et mots clés, départements et rayon. Vient ensuite une étape facultative d'ajout de pièces, avec l'état réel de la connexion et des sources. Vous choisissez le profil d'exemple « Charpente bois — 35/22 » ou un profil vide. Si l'ancien dossier `Documents\Veille Bois` existe, l'assistant propose de reprendre vos données.
2. **Tableau de bord** — nouvelles opportunités, échéances proches, dossiers à préparer, réponses à relancer. Tous les compteurs sont calculés à partir de votre base locale.
3. **Opportunités** — plusieurs départements, mots clés, synonymes, exclusions et période de publication. La recherche BOAMP tourne en arrière-plan : progression, annulation, erreurs visibles. Le tableau se filtre par source, suivi et échéance. Chaque fiche montre son **origine**, sa **méthode d'obtention**, un **score expliqué** et un **niveau de confiance**.
4. **Ajouter une demande** — saisie manuelle et assistant d'import CSV : correspondance des colonnes, contrôle ligne par ligne, doublons, erreurs. S'y ajoutent l'import de notifications `.eml` et l'historique des imports.
5. **Dossier entreprise** — coordonnées, présentation et pièces copiées dans l'application (empreinte SHA-256), export ZIP.
6. **Répondre** — le parcours dépend du canal : dépôt sur le profil acheteur (marché public), brouillon de courriel avec les vraies pièces (contact autorisé) ou messagerie de la plateforme.
7. **Sources**, **Paramètres** (thème, messagerie, recherche automatique, sauvegarde, restauration, migration) et **Aide** recherchable (F1 depuis chaque page).
8. **Recherche automatique quotidienne** — *Paramètres → Recherche automatique quotidienne* : chaque jour à l'heure choisie, la recherche BOAMP est relancée et une notification Windows signale les nouvelles opportunités. Si l'heure est passée alors que l'application était fermée, la recherche est faite à l'ouverture suivante. En option, une tâche du Planificateur de tâches Windows (`VigiOffres --recherche-auto`) fait la recherche même quand l'application est fermée, tant que l'ordinateur est allumé et la session ouverte.
9. **Informations légales** — mentions légales, CGV et confidentialité (« vos données restent sur votre ordinateur »), et contact : **Guardian Wall — contact@guardianwall.fr**. Les champs marqués [à compléter] (statut, SIRET, adresse, prix, médiateur) sont à renseigner avant toute vente.

Le copyright **© 2026 Riadh BEN KHALED** et le numéro de version apparaissent en bas de la barre de navigation et dans la barre d'état.

### Statuts

À qualifier · À contacter · Dossier en préparation · Brouillon prêt · **Envoyé / Déposé (confirmé)** · À relancer · Gagné · Écarté.
Créer un brouillon ou ouvrir une messagerie ne fait **jamais** passer une fiche à « Envoyé ». C'est vous qui confirmez l'envoi ou le dépôt, après une question de confirmation. Chaque changement est daté dans l'historique.

### Raccourcis clavier

| Raccourci | Action |
|---|---|
| Ctrl+1 … Ctrl+9 | Pages du menu, dans l'ordre |
| F5 | Recherche BOAMP |
| Échap | Annuler la recherche en cours |
| Ctrl+F | Filtrer les fiches |
| Ctrl+N | Ajouter une demande |
| Ctrl+S | Enregistrer la demande saisie |
| Ctrl+Maj+L | Thème sombre / clair |
| F1 | Aide de la page affichée |

---

## 3. Données, sauvegarde et migration

| Élément | Emplacement |
|---|---|
| Base SQLite | `Documents\VigiOffres\vigioffres.db` |
| Préférences (aucun mot de passe) | `Documents\VigiOffres\parametres.json` |
| Pièces copiées | `Documents\VigiOffres\pieces\` |
| Brouillons `.eml` | `Documents\VigiOffres\brouillons\` |
| Sauvegardes ZIP | `Documents\VigiOffres\sauvegardes\` |
| Journal technique | `Documents\VigiOffres\journaux\` |

**Sauvegarde :** *Paramètres → Sauvegarder maintenant*. L'application crée une archive ZIP cohérente, avec une copie de la base faite par l'API de sauvegarde SQLite. Copiez-la ensuite sur un support externe.
**Restauration :** *Paramètres → Restaurer une sauvegarde…*. L'état actuel est d'abord sauvegardé automatiquement (`avant_restauration_….zip`).

### Migration V2 / V3 (`Documents\Veille Bois`)

- L'ancien dossier est d'abord archivé dans `sauvegardes\VeilleBois_avant_migration_….zip`.
- `veille.db` est lue **depuis une copie** : l'original n'est jamais ouvert en écriture. `profil.json`, les pièces et `marche_pilot.json` ne sont ni modifiés ni supprimés.
- Sont repris : fiches (avec statut), flux RSS, profil, pièces (copiées) et préférences V3 (départements, mots clés, messagerie).
- Correspondance des statuts : « Dossier prêt » → « Dossier en préparation » ; « Réponse préparée » → « Brouillon prêt » (ce n'était pas un envoi) ; « Envoyé » → « Envoyé / Déposé (confirmé) ».
- Les pièces V2 dont le fichier n'existe plus apparaissent comme « Introuvable — à remplacer », avec leur chemin d'origine.
- Une date limite non reconnue est conservée dans les notes de la fiche.
- Les demandes privées reprises ne sont pas marquées « contact direct autorisé ». Cochez l'autorisation dans la fiche si le client vous l'a donnée.
- Relancer la reprise n'ajoute que les fiches absentes (aucun doublon).

---

## 4. Limites connues (à lire)

- **Plateformes privées** (Travaux.com, Habitatpresto, AlloVoisins…) : **aucune synchronisation automatique**. Aucune API officielle ni accès autorisé n'est disponible, et VigiOffres ne contourne ni connexion, ni abonnement, ni CAPTCHA. Les demandes arrivent par import CSV, notification `.eml`, flux RSS/Atom que vous fournissez, ou saisie. « Ouvrir mon espace » ouvre seulement votre navigateur. Une interface de connecteur (`sources/connectors.py`) est prête pour une future API officielle ; aucun connecteur n'est actif.
- **Une notification ne vaut pas autorisation de contact** hors plateforme : la fiche indique le canal prévu.
- **BOAMP** : un avis peut annoncer plusieurs départements. Le lieu exact d'un lot n'est pas toujours publié dans les données : VigiOffres affiche alors « Lieu à vérifier » et n'invente jamais de lieu. Le téléchargement et l'analyse du **DCE ne sont pas implémentés**. Les pièces exigées sont à vérifier dans le règlement de consultation. Les rectificatifs sont rattachés à l'avis d'origine quand les données indiquent l'avis lié ; sinon ils apparaissent comme fiche « Avis rectificatif ».
- **Messageries :** seul **Outlook classique** (installé sur le poste) reçoit un brouillon avec les pièces déjà jointes, par automatisation locale ; rien n'est envoyé. La messagerie par défaut, Gmail, Outlook Web et Orange Mail ne permettent pas de joindre des fichiers automatiquement : le dossier des pièces s'ouvre pour les ajouter à la main. Un fichier `.eml` complet est toujours enregistré ; selon le logiciel, il peut s'ouvrir en lecture seule.
- **Taille des pièces :** 25 Mo par pièce et 20 Mo au total pour un brouillon de courriel.

---

## 5. Choix techniques

- **PySide6 / Qt Widgets** plutôt que Tkinter ou Streamlit. C'est une vraie application de bureau Windows : tableaux riches, formulaires, boîtes de dialogue, navigation clavier, tâches de fond `QThread`, thèmes et haute densité d'affichage (125 %, 150 %). Le packaging PyInstaller est éprouvé.
- **Licence Qt :** PySide6 (Qt for Python) est distribué sous **LGPLv3** (ou licence commerciale). Distribuer l'EXE est compatible avec la LGPL si les bibliothèques Qt restent des fichiers séparés et remplaçables. C'est le cas du mode dossier (`--onedir`) utilisé par `build_windows.ps1`. Joignez la mention de licence LGPL et n'utilisez pas `--onefile` pour une diffusion à des tiers sans vérification juridique.
- Pictogrammes : tracés **Lucide** (licence ISC), recolorés par thème. Logo original : repère radar et losange « opportunité ».
- Architecture :

```
VigiOffres/
  run_vigioffres.py          lanceur (source et PyInstaller)
  LANCER_VIGIOFFRES.bat      installation + lancement en double-clic
  build_windows.ps1           tests + construction de l'EXE
  pyproject.toml / requirements.txt / requirements-dev.txt
  vigioffres/
    main.py  context.py  paths.py
    domain/     departments, dates (heure de Paris), models (statuts, canaux), scoring, validation
    sources/    boamp (API officielle), private_import (CSV, .eml, RSS/Atom), connectors
    services/   opportunities, search_service, imports, documents, drafts, profile, backup, network
    storage/    db (SQLite + migrations versionnées), settings, migration (V2/V3)
    ui/         main_window, theme, widgets, icons, workers (QThread), table_model, detail_panel,
                dept_selector, onboarding, help_content, pages/…
    assets/     logo.svg, logo.png, logo_256.png, app.ico
  tests/        règles métier, imports, pièces, brouillons, migration, contraste, parcours UI
  tools/        capture.py (captures), overflow_check.py (débordements), smoke.py
  docs/         DESIGN_SYSTEM.md, CHECKLIST_VISUELLE.md, RESULTATS_TESTS.md, captures/
```

La collecte, le stockage, l'analyse, le score, les pièces, la préparation d'envoi et l'interface sont séparés. L'interface ne fait jamais de requête réseau dans son propre fil.

---

## 6. Sécurité et confidentialité

- Aucun mot de passe ni jeton n'est demandé ou stocké ; aucun envoi SMTP.
- Les liens importés ne sont jamais ouverts automatiquement. Seuls `http(s)://` sont acceptés, et un bandeau prévient à chaque ouverture du navigateur.
- Flux RSS/Atom : HTTPS obligatoire, 2 Mo maximum, délai de 18 s ; les XML mal formés et les documents déclarant un DOCTYPE ou des entités sont refusés.
- Notifications `.eml` : lecture prudente, HTML débarrassé des scripts, aucun contenu exécuté.
- Requête BOAMP construite uniquement à partir de codes de département validés.
