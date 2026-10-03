# Guide complet d’utilisation de VigiOffres

Version 4.0.0 — Application Windows — © 2026 Riadh BEN KHALED / Guardian Wall.

VigiOffres aide les indépendants, artisans et PME à trouver des marchés publics, centraliser leurs demandes privées, préparer leurs réponses et suivre leurs opportunités. Le profil bois proposé au démarrage est un exemple modifiable : vous pouvez utiliser l’application pour d’autres métiers et départements.

## Sommaire

1. [Installer, mettre à jour et désinstaller](#1-installer-mettre-à-jour-et-désinstaller)
2. [Configurer le premier lancement](#2-configurer-le-premier-lancement)
3. [Se repérer dans l’application](#3-se-repérer-dans-lapplication)
4. [Rechercher et qualifier les marchés publics](#4-rechercher-et-qualifier-les-marchés-publics)
5. [Ajouter et importer les demandes privées](#5-ajouter-et-importer-les-demandes-privées)
6. [Utiliser les sources et les flux](#6-utiliser-les-sources-et-les-flux)
7. [Préparer le dossier entreprise](#7-préparer-le-dossier-entreprise)
8. [Préparer une réponse](#8-préparer-une-réponse)
9. [Suivre les statuts et les relances](#9-suivre-les-statuts-et-les-relances)
10. [Programmer la veille quotidienne](#10-programmer-la-veille-quotidienne)
11. [Sauvegarder, restaurer et changer de poste](#11-sauvegarder-restaurer-et-changer-de-poste)
12. [Reprendre les anciennes versions](#12-reprendre-les-anciennes-versions)
13. [Raccourcis et personnalisation](#13-raccourcis-et-personnalisation)
14. [Dépannage et questions fréquentes](#14-dépannage-et-questions-fréquentes)
15. [Confidentialité, limites et assistance](#15-confidentialité-limites-et-assistance)

## 1. Installer, mettre à jour et désinstaller

### Installation

L’installateur fourni cible Windows 64 bits. Python et les bibliothèques graphiques sont embarqués : leur installation séparée n’est pas nécessaire. Une connexion Internet est nécessaire pour les recherches BOAMP, les flux et les services externes ; les fiches déjà enregistrées restent consultables hors ligne.

1. Téléchargez `VigiOffres_Setup_4.0.0.exe` depuis la release officielle du dépôt.
2. Vérifiez que le nom du fichier et la version correspondent à la release. L’empreinte publiée dans `SHA256SUMS.txt` permet de vérifier son intégrité.
3. Double-cliquez sur le fichier, puis sur **Installer**.
4. À la fin, choisissez **Lancer VigiOffres maintenant**, ou utilisez le raccourci Bureau / menu Démarrer.

L’installation se fait pour votre utilisateur, sans droits administrateur, dans `%LOCALAPPDATA%\Programs\VigiOffres`.

Si SmartScreen signale un éditeur non reconnu, vérifiez d’abord la provenance et l’empreinte du fichier. L’installateur non signé peut déclencher cet avertissement ; si vous avez confirmé sa provenance, l’interface Windows peut proposer **Informations complémentaires → Exécuter quand même**. Si votre organisation interdit cette action, demandez à son service informatique.

Vérification de l’empreinte dans PowerShell :

```powershell
Get-FileHash "$env:USERPROFILE\Downloads\VigiOffres_Setup_4.0.0.exe" -Algorithm SHA256
```

Comparez le résultat avec `SHA256SUMS.txt`. Pour une installation silencieuse : `VigiOffres_Setup_4.0.0.exe /S`.

### Mise à jour

Sauvegardez vos données, fermez l’application, puis lancez l’installateur de la nouvelle version. L’installateur remplace l’application ; les données de `Documents\VigiOffres` sont conservées. Le guide correspond à la version 4.0.0 : consultez les notes de chaque nouvelle release.

### Désinstallation

Ouvrez **Paramètres Windows → Applications → Applications installées → VigiOffres → Désinstaller**. Les données restent dans `Documents\VigiOffres`. Conservez-les si vous prévoyez de réinstaller l’application ; leur suppression manuelle efface vos fiches, pièces et brouillons.

## 2. Configurer le premier lancement

L’assistant vous accompagne dans quatre étapes :

1. **Entreprise** : renseignez votre entreprise ou choisissez le profil d’exemple « Charpente bois — 35/22 » / un profil vide.
2. **Coordonnées** : renseignez vos coordonnées professionnelles, utilisées pour préparer vos réponses.
3. **Activités et mots clés** : choisissez des termes concrets correspondant à votre métier.
4. **Départements et rayon** : définissez la zone que vous souhaitez surveiller.

L’ajout de pièces est facultatif. Vous pouvez terminer la configuration et compléter le dossier plus tard. Si des données anciennes sont détectées dans `Documents\Veille Bois`, une reprise vous est proposée.

Pour corriger les informations ensuite, utilisez **Dossier entreprise** pour les coordonnées et **Opportunités** pour les critères de recherche. **Paramètres → Relancer l’assistant** permet de revoir le parcours initial.

Exemple de départ : choisissez deux départements que vous couvrez réellement et quelques mots clés comme « charpente, bardage, pergola ». Élargissez ensuite si les résultats sont insuffisants.

## 3. Se repérer dans l’application

| Page | Utilité |
|---|---|
| Tableau de bord | Repérer les nouveautés, échéances proches, dossiers à préparer et réponses à relancer. |
| Opportunités | Rechercher sur BOAMP, filtrer les fiches et consulter leur détail. |
| Ajouter une demande | Saisir une demande privée, importer un CSV ou des notifications `.eml`. |
| Dossier entreprise | Enregistrer les coordonnées, gérer les pièces et exporter un dossier ZIP. |
| Répondre | Préparer le parcours adapté au marché public, au contact direct ou à la plateforme. |
| Sources | Comprendre les sources, ouvrir les espaces privés et utiliser les flux fournis. |
| Paramètres | Choisir le thème et la messagerie, programmer la recherche, sauvegarder et restaurer. |
| Aide | Rechercher une explication ; F1 ouvre l’aide liée à la page affichée. |
| Informations légales | Consulter les mentions, les CGV, la confidentialité et le contact. |

Les compteurs du tableau de bord utilisent votre base locale. Un tableau vide au premier lancement est normal : lancez une recherche ou ajoutez une demande.

## 4. Rechercher et qualifier les marchés publics

### Lancer une recherche

1. Ouvrez **Opportunités**.
2. Sélectionnez un ou plusieurs départements.
3. Saisissez les mots clés séparés par des virgules.
4. Complétez les synonymes et les exclusions si nécessaire.
5. Ajustez la période de publication.
6. Cliquez sur **Rechercher sur BOAMP**, ou appuyez sur **F5**.

La recherche se déroule en arrière-plan. Suivez la progression ; utilisez **Annuler** ou **Échap** si nécessaire. Les erreurs sont affichées pour vous permettre de réessayer.

### Comprendre une fiche

Consultez l’intitulé, l’acheteur, les dates, les départements, les liens, la source, la méthode d’obtention et le score expliqué. Un terme trouvé dans le titre a plus de poids qu’un terme retrouvé seulement dans un descripteur BOAMP. Les synonymes contribuent moins que les mots clés principaux ; les exclusions écartent les annonces correspondantes.

Le score est une aide au tri. Il ne garantit ni l’éligibilité de votre entreprise ni la pertinence de tous les lots. Lisez toujours l’avis et le dossier de consultation.

Les dates sont affichées à l’heure de Paris. Les indicateurs J-3, J-7, etc. vous aident à repérer l’urgence. Un avis peut mentionner plusieurs départements : si le lieu d’exécution n’est pas disponible, **Lieu à vérifier** apparaît. Vérifiez alors l’avis et les lots.

Filtrez le tableau par source, suivi ou échéance et utilisez **Ctrl+F** pour retrouver une fiche. Les rectificatifs sont rattachés à l’avis initial lorsque les données permettent ce lien ; sinon ils apparaissent séparément.

## 5. Ajouter et importer les demandes privées

### Saisie manuelle

1. Ouvrez **Ajouter une demande → Saisie manuelle**, ou utilisez **Ctrl+N**.
2. Renseignez l’intitulé obligatoire et les informations disponibles : source, département / code postal, client, lien, date limite, courriel, téléphone et description.
3. Utilisez `JJ/MM/AAAA` ou `JJ/MM/AAAA HH:MM` pour la date limite.
4. Cochez l’autorisation de contact direct par courriel uniquement si le client vous l’a donnée.
5. Cliquez sur **Enregistrer la demande** ou utilisez **Ctrl+S**.

La fiche apparaît dans **Opportunités**. Aucun message n’est envoyé lors de son enregistrement. Un lieu ou une date non reconnus doivent être vérifiés.

### Import CSV

Exportez votre tableur ou les demandes de votre plateforme en CSV avec une ligne d’en-tête. Le séparateur et les encodages UTF-8 / Windows-1252 sont détectés automatiquement.

1. Ouvrez **Ajouter une demande → Import CSV**.
2. Choisissez la source et cliquez sur **Choisir un fichier CSV…**.
3. Associez les colonnes de votre fichier aux champs proposés. L’intitulé doit être associé ; les autres colonnes peuvent être ignorées.
4. Cliquez sur **Vérifier les lignes** et lisez les détails : **Prête**, **À vérifier**, **Doublon — ignoré**, **Erreur**.
5. Corrigez les problèmes dans le fichier ou la correspondance, puis importez les lignes valides.

Les doublons sont ignorés et les erreurs conservées dans **Historique des imports**. Les lignes « À vérifier » peuvent contenir des données incomplètes : contrôlez les fiches après import. N’interprétez pas une adresse courriel importée comme une autorisation de contact.

### Notifications `.eml`

Enregistrez une notification reçue dans votre messagerie au format `.eml`, puis ouvrez **Ajouter une demande → Notifications .eml → Choisir des fichiers .eml…**. Vérifiez l’aperçu avant de cliquer sur **Importer**.

L’application lit les fichiers sélectionnés : elle n’accède pas à votre boîte mail et n’ouvre pas les liens automatiquement. Une notification issue d’une plateforme ne vous autorise pas à contacter son client hors plateforme.

### Historique

Consultez **Historique des imports** pour retrouver la date, le type, la source ou le fichier, le nombre de lignes, les fiches ajoutées et les doublons / erreurs.

## 6. Utiliser les sources et les flux

**BOAMP** est la source officielle recherchée automatiquement. Les espaces privés tels que Travaux.com, Habitatpresto et AlloVoisins ne sont pas synchronisés automatiquement : **Ouvrir mon espace** ouvre votre navigateur. Utilisez les exports autorisés, les notifications ou la saisie manuelle pour centraliser ces demandes.

Pour un flux RSS / Atom, renseignez une adresse HTTPS dans **Sources**, puis utilisez les commandes de lecture proposées. Vérifiez les demandes obtenues. Un flux est lu à votre demande ; il ne donne pas accès à une plateforme payante ni à des informations nécessitant une connexion.

Les flux doivent rester accessibles et valides. Les flux trop volumineux, XML mal formés ou contenant des déclarations interdites sont refusés. En cas d’erreur, vérifiez l’adresse et l’accès depuis votre navigateur.

## 7. Préparer le dossier entreprise

Dans **Dossier entreprise**, complétez les coordonnées et une présentation courte : compétences, zone d’intervention, références et qualifications. Cliquez sur **Enregistrer les coordonnées**.

Ajoutez ensuite les pièces utiles avec **Ajouter des pièces**, par exemple Kbis, attestations URSSAF / fiscale, assurances ou références. Chaque pièce est copiée dans `Documents\VigiOffres\pieces` : déplacer l’original ne rend pas la copie indisponible. Les fichiers sont identifiés par leur empreinte SHA-256 ; un contenu identique n’est pas recopié et des noms identiques ne s’écrasent pas.

- Taille maximale : **25 Mo par pièce**.
- Sélectionnez une pièce pour l’ouvrir, la remplacer ou changer sa catégorie.
- Une pièce **Introuvable — à remplacer** doit être remplacée avant de l’utiliser.
- **Retirer** peut enlever la pièce de la liste en conservant le fichier, ou supprimer sa copie selon votre choix. Lisez les confirmations, notamment si un brouillon l’utilise.
- **Exporter en ZIP** produit un dossier avec la présentation et les pièces disponibles. Une pièce manquante n’est pas incluse ; l’application le signale.

Vérifiez la validité et les dates de vos attestations. La liste des pièces habituellement demandées est indicative : le règlement de consultation détermine les pièces de chaque marché.

## 8. Préparer une réponse

Sélectionnez l’opportunité concernée et ouvrez **Répondre**. Le parcours dépend de son canal.

### Marché public

1. Ouvrez l’avis BOAMP.
2. Ouvrez le profil acheteur et téléchargez le DCE (dossier de consultation des entreprises).
3. Lisez le RC (règlement de consultation) : lots, pièces, visite éventuelle, critères et heure limite.
4. Préparez les documents demandés et vérifiez leur contenu.
5. Déposez l’offre sur le profil acheteur selon les instructions de la consultation.
6. Conservez l’accusé de réception, puis confirmez le dépôt dans VigiOffres.

Le téléchargement et l’analyse automatiques du DCE ne sont pas disponibles. La checklist ne remplace pas le RC. Créer un courriel ne constitue pas un dépôt sur le profil acheteur.

### Demande privée avec contact direct autorisé

Vérifiez le destinataire, personnalisez le message et sélectionnez les pièces pertinentes. Préparez le brouillon, relisez-le dans votre messagerie, ajoutez les pièces si nécessaire, puis envoyez vous-même le message. Confirmez ensuite l’envoi dans VigiOffres.

### Demande à traiter sur une plateforme

Préparez le texte, copiez-le, ouvrez la demande sur la plateforme et ajoutez les pièces selon son interface. Effectuez vous-même l’envoi sur cette plateforme, puis confirmez-le dans VigiOffres.

### Choisir la messagerie

Le choix se fait dans **Paramètres**.

| Messagerie | Préparation |
|---|---|
| Outlook classique installé | Ouvre un brouillon avec les pièces jointes lorsque l’automatisation locale est disponible. |
| Messagerie par défaut | Prépare un message ; ajoutez les pièces depuis le dossier ouvert. |
| Gmail, Outlook Web, Orange Mail | Ouvre le service dans le navigateur ; le texte est copié et les pièces doivent être ajoutées manuellement. |

Un fichier `.eml` contenant le texte et les pièces est enregistré dans `Documents\VigiOffres\brouillons`. Certaines messageries l’ouvrent en lecture seule : créez alors un nouveau message et joignez les pièces. Le total des pièces d’un brouillon est limité à **20 Mo**. Vérifiez également les limites de votre messagerie.

## 9. Suivre les statuts et les relances

| Statut | Utilisation |
|---|---|
| À qualifier | Vérifier l’intérêt et les conditions de la demande. |
| À contacter | Préparer la prise de contact par le canal autorisé. |
| Dossier en préparation | Réunir les documents et préparer l’offre. |
| Brouillon prêt | Le message est préparé, sans confirmation d’envoi. |
| Envoyé / Déposé (confirmé) | Vous avez confirmé l’action réalisée hors de l’application. |
| À relancer | Une suite ou une relance reste à effectuer. |
| Gagné | Vous avez obtenu le marché ou la demande. |
| Écarté | Vous ne poursuivez pas l’opportunité. |

Chaque changement est daté dans l’historique. Ouvrir une messagerie ou créer un brouillon ne confirme jamais l’envoi. Utilisez les notes de la fiche pour conserver les informations utiles et consultez régulièrement les échéances du tableau de bord.

Routine conseillée : consulter les nouveautés, qualifier les fiches pertinentes, traiter les échéances proches, préparer les réponses, puis mettre à jour les statuts après vos actions réelles.

## 10. Programmer la veille quotidienne

Dans **Paramètres → Recherche automatique quotidienne**, activez la recherche et choisissez l’heure. Elle utilise vos critères BOAMP. Activez la notification Windows si vous souhaitez être prévenu des nouveautés.

Si l’application reste ouverte, la recherche démarre à l’heure choisie. Si elle était fermée, la recherche prévue est rattrapée à l’ouverture suivante, une seule fois par jour.

Pour rechercher aussi application fermée, cliquez sur **Programmer aussi application fermée**. Une tâche Windows est créée : l’ordinateur doit être allumé et la session ouverte. **Retirer la tâche Windows** désactive cette programmation externe. Si vous changez l’heure, reprogrammez également la tâche Windows pour aligner les horaires.

La veille ajoute des fiches à qualifier : elle ne répond pas aux demandes. Si elle ne se déclenche pas, vérifiez l’activation, les critères, la connexion, les notifications Windows et l’état de la tâche dans le Planificateur de tâches.

## 11. Sauvegarder, restaurer et changer de poste

### Emplacement des données

| Élément | Dossier ou fichier |
|---|---|
| Base des fiches | `Documents\VigiOffres\vigioffres.db` |
| Préférences | `Documents\VigiOffres\parametres.json` |
| Pièces | `Documents\VigiOffres\pieces` |
| Brouillons | `Documents\VigiOffres\brouillons` |
| Sauvegardes ZIP | `Documents\VigiOffres\sauvegardes` |
| Journaux techniques | `Documents\VigiOffres\journaux` |

Le dossier peut être différent si un lancement technique définit `VIGIOFFRES_HOME`. Le chemin réellement utilisé est affiché dans **Paramètres**.

### Sauvegarde

Cliquez sur **Paramètres → Sauvegarder maintenant**. Une archive ZIP cohérente est créée avec la base et les données de l’application. Copiez-la sur un support externe : une sauvegarde laissée sur le même disque ne protège pas contre sa panne.

Sauvegardez régulièrement, avant une mise à jour, une migration ou un changement de poste. Les archives contiennent vos données professionnelles et vos pièces : protégez leur accès.

### Restauration

Cliquez sur **Paramètres → Restaurer une sauvegarde…**, choisissez le ZIP et lisez la confirmation. La restauration remplace l’état actuel ; une sauvegarde préalable `avant_restauration_….zip` est créée automatiquement. Vérifiez ensuite les fiches, coordonnées et pièces restaurées.

### Changer d’ordinateur

Créez une sauvegarde sur l’ancien poste, transférez le ZIP, installez VigiOffres sur le nouveau et restaurez l’archive. Vérifiez vos données et reprogrammez la tâche Windows si vous l’utilisiez. Une autre méthode consiste à copier tout `Documents\VigiOffres`, application fermée ; utilisez de préférence la sauvegarde intégrée.

## 12. Reprendre les anciennes versions

La reprise de MarchéPilot / Veille Bois V2 ou V3 recherche `Documents\Veille Bois`. Utilisez l’assistant initial ou la commande de migration dans **Paramètres**.

Avant la reprise, l’ancien dossier est archivé. La base ancienne est lue depuis une copie ; l’original n’est pas modifié. Les fiches, flux, profil, pièces disponibles et préférences reconnues sont repris.

- « Dossier prêt » devient « Dossier en préparation ».
- « Réponse préparée » devient « Brouillon prêt ».
- « Envoyé » devient « Envoyé / Déposé (confirmé) ».
- Une pièce ancienne absente est signalée comme introuvable : remplacez-la.
- Une date limite non reconnue reste dans les notes : corrigez-la après contrôle.
- Les demandes privées reprises n’obtiennent pas automatiquement l’autorisation de contact direct.

Lisez le rapport de migration. Une nouvelle reprise ajoute seulement les fiches absentes pour éviter les doublons.

## 13. Raccourcis et personnalisation

| Raccourci | Action |
|---|---|
| Ctrl+1 à Ctrl+9 | Ouvrir les pages dans l’ordre du menu. |
| F5 | Lancer la recherche BOAMP. |
| Échap | Annuler la recherche en cours. |
| Ctrl+F | Filtrer les opportunités. |
| Ctrl+N | Ajouter une demande. |
| Ctrl+S | Enregistrer la demande saisie. |
| Ctrl+Maj+L | Basculer entre thème clair et sombre. |
| F1 | Afficher l’aide de la page. |
| Tab / Maj+Tab | Parcourir les champs et boutons. |
| Entrée / Espace | Activer le contrôle sélectionné. |

Le thème et la messagerie se choisissent aussi dans **Paramètres**. Recherchez un mot dans **Aide** pour retrouver une rubrique.

## 14. Dépannage et questions fréquentes

| Problème | Vérifications et actions |
|---|---|
| L’application ne démarre pas | Fermez les autres instances, relancez depuis le menu Démarrer et consultez les journaux. Sauvegardez les données avant de réinstaller. |
| BOAMP inaccessible / hors ligne | Vérifiez la connexion avec le bouton prévu et votre accès Internet. Réessayez plus tard si le service est indisponible. |
| Trop de requêtes | Attendez avant de relancer ; BOAMP peut limiter le débit. |
| Aucun résultat | Élargissez les départements, la période ou les mots clés ; réduisez les exclusions trop larges. |
| Résultats peu pertinents | Consultez l’explication du score et ajustez les termes ; lisez les lots avant de décider. |
| Lieu à vérifier | Consultez le lieu d’exécution dans l’avis / DCE ; le département de publication n’est pas toujours celui du chantier. |
| CSV illisible ou mal associé | Vérifiez l’en-tête, le séparateur, l’encodage et la correspondance des colonnes. Corrigez les lignes en erreur. |
| Doublon ignoré | Vérifiez la fiche déjà présente avant de réimporter. |
| Pièce introuvable | Sélectionnez-la dans Dossier entreprise, puis utilisez Remplacer. |
| Pièce trop volumineuse | Réduisez le fichier sous 25 Mo ; limitez aussi les pièces d’un brouillon à 20 Mo au total. |
| Outlook classique non détecté | Choisissez une autre messagerie et utilisez le texte / les pièces du brouillon enregistré. Le nouvel Outlook ne remplace pas cette automatisation classique. |
| `.eml` en lecture seule | Créez un nouveau message dans votre messagerie et ajoutez les pièces manuellement. |
| Base verrouillée | Fermez les autres fenêtres / instances de VigiOffres, puis réessayez. |
| Pas de notification | Vérifiez l’option dans VigiOffres, les autorisations de notification Windows et le mode Ne pas déranger. |
| Recherche automatique absente | Vérifiez activation, heure, connexion et critères ; pour la tâche externe, vérifiez ordinateur allumé, session ouverte et programmation Windows. |
| Sauvegarde impossible | Vérifiez l’espace libre et l’accès au dossier de données. |
| Restauration refusée | Choisissez une sauvegarde VigiOffres valide et conservez l’archive d’origine ; consultez le message d’erreur. |

**Faut-il un compte VigiOffres ?** Non. Les services tiers peuvent demander leur propre compte lorsque vous les ouvrez.

**Les plateformes privées sont-elles recherchées automatiquement ?** Non. Utilisez leurs exports autorisés, notifications, flux disponibles ou la saisie.

**L’application envoie-t-elle mes réponses ?** Non. Elle prépare les éléments ; vous envoyez / déposez depuis le service concerné, puis confirmez l’action.

**Puis-je utiliser plusieurs postes simultanément sur la même base ?** Le fonctionnement documenté est local. Pour changer de poste, utilisez sauvegarde / restauration ; ce guide ne décrit pas une synchronisation multi-utilisateur.

## 15. Confidentialité, limites et assistance

Les fiches, pièces, préférences et brouillons restent sur votre ordinateur. Les recherches BOAMP, les flux et l’ouverture de services externes nécessitent des échanges réseau. Aucun mot de passe de messagerie ni envoi SMTP n’est demandé. Protégez votre session Windows et le dossier de données.

VigiOffres ne contourne pas les connexions, abonnements ou CAPTCHA des plateformes. Il ne télécharge ni n’analyse automatiquement les DCE, ne garantit pas l’exhaustivité des annonces, et ne décide pas de votre éligibilité. Vérifiez les informations sur la source et respectez le canal de réponse prévu.

L’onglet **Informations légales** contient des informations complémentaires. Le code source déclare une licence propriétaire : un dépôt public ne constitue pas une licence libre. Consultez les conditions applicables auprès de l’éditeur.

Assistance : **Guardian Wall — contact@guardianwall.fr**. Indiquez la version de VigiOffres, votre version de Windows, la page concernée, les étapes reproduisant le problème et le message exact. Retirez les coordonnées de clients, pièces confidentielles et données personnelles avant de partager une capture ou un journal. Ne publiez pas votre base ni vos sauvegardes sur GitHub.
