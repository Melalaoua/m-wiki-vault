---
type: source
title: "OAD(handoff) - React Native ou ODK"
citekey: notes2025oadhandoff
source_type: article
captured: 2025-09-09
site: notes
url: 
aliases: []
tags: [source, phd]
updated: 2025-09-09
status: developing
---

# OAD(handoff) - React Native ou ODK

Original: [[raw/notes/OAD(handoff) - React Native ou ODK]]

## [[phd/wiki/concepts/open-data-kit|ODK]]
Plateformes de collecte de données avec des formulaires sous forme XLS (excel, google sheets) ou sous format web.

les formulaires peuvent contenir : 
- photos
- GPS
- calculs
- datasets externes
- multiples languages
- ...

Les données peuvent être collectées en ligne ou offline, tout est synchronisés lorsqu'une connection est retrouvée. (See [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]])

Possibilité de connecter ODK avec python, excel, power bi, R.

Peut être self-host ou hébergé sur des serveurs distant.

1. Trouver un serveur central (soit le cloud) ou notre propre serveur.
2. Obtenir l'application de collecte (google play store or APK)
3. Upload les formulaires sur le serveur central.
4. Remplir les questionnaires
5. Envoyer les données au serveur central.

La construction de l'app serait rapide, en 1 mois. Elle serait très stable, fonctionnel immédiatement mais un sacrifice important sur le design, l'UX, le choix du fonctionnement de l'application. 

### Points négatifs.
- Si on ne paie pas, pas d'accès aux entités, seulement des formulaires straightforward.
- Quid de la liberté sur le design des formulaires ?
- design statique, pas d'interactivité / dynamicité.

## [[phd/wiki/concepts/react-native|React native]]

Construction de zéro de l'application, laissant un choix sur la forme, le design de l'application.

Nécessite l'apprentissage d'un nouveau langage de programmation, plus coûteux et long. 4 mois est suffisant.

Permet d'explorer plus de choix artistiques, fonctionnels. 

Nécessite un développement full-stack : de l'application au serveur. De l'infrastructure à la sécurité/juridiction des données. Un vrai travail d'ingénierie.

# A faire :
- wireframe & maquette.
- 300€ par tablette trouver un modèle de tablette android. ~mi-octobre.
- vol de tablette.
- quid de l'IA ? faire en sorte avec peu de moyen on ait le meilleur diagnostic et la meilleure prise en charge = aide à la décision et réalisable / optimal.
- réduire la prescription.
- intérêt économique.
- réunion avec Bangui à prévoir.
- [[phd/wiki/entities/souma|Souma]] ; project manager.
- [[phd/wiki/entities/romaric|Romaric]] ; un point 0 dans le projet/ responsable
- lire les compte-rendus

## Key claims

- ODK allows for a rapid, 1-month development cycle that yields a stable application, but requires significant sacrifices in design and user experience. ([[raw/notes/OAD(handoff) - React Native ou ODK#ODK]]) — "La construction de l'app serait rapide, en 1 mois. Elle serait très stable, fonctionnel immédiatement mais un sacrifice important sur le design, l'UX"
- Using React Native gives full control over the application's design and functionality but requires learning a new language and a roughly 4-month full-stack development cycle. ([[raw/notes/OAD(handoff) - React Native ou ODK#React native]]) — "Construction de zéro de l'application, laissant un choix sur la forme, le design de l'application... 4 mois est suffisant... Nécessite un développement full-stack"
- The integration of AI in the project aims to provide optimal diagnostic and decision-making support despite limited resources. ([[raw/notes/OAD(handoff) - React Native ou ODK#A faire :]]) — "faire en sorte avec peu de moyen on ait le meilleur diagnostic et la meilleure prise en charge = aide à la décision et réalisable / optimal."
