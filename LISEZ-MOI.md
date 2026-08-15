# SurH40 — mémoire du projet

Fichier de reprise. À joindre à `index.html` si tu redémarres une conversation
avec Claude : il contient les décisions et leurs raisons, pas seulement les
fonctionnalités.

---

## 1. Ce que contient ce dossier

| Fichier | Rôle |
|---|---|
| `index.html` | L'application entière : code, style, données, tout est dedans |
| `manifest.webmanifest` | Nom, icône, couleurs pour l'installation |
| `sw.js` | Fonctionnement hors ligne. **Incrémenter `CACHE` à chaque mise à jour** |
| `icon-192 / 512 / apple-touch-icon` | Icônes (pointe de lance dorée sur basalte) |

**Mise en ligne** : dépôt GitHub public → Settings → Pages → branche `main` / root.
**Mise à jour** : remplacer `index.html` et `sw.js`, fermer complètement l'appli, rouvrir deux fois.
**Les données ne sont jamais dans les fichiers** : elles vivent dans le navigateur de chaque appareil.

---

## 2. L'intention

Une application d'habitudes pour un homme de 38 ans, père de trois enfants,
dont l'objectif est d'être présent et en forme sur le long terme.
Nom : **SurH40**, pour « Sur-homme à 40 ans ».

Trois principes ont guidé chaque décision :

1. **La friction tue les habit trackers.** Le premier facteur d'abandon n'est pas
   le manque de fonctions mais le sur-tracking. D'où : tout se coche depuis
   l'écran d'accueil, et le conseil constant de rester sous 5 ou 6 habits actives.
2. **L'outil ne doit jamais punir l'absence.** Une journée non renseignée ne
   génère aucun écart. Le jour où l'appli devient un tribunal, on ne l'ouvre plus.
3. **L'identité plutôt que les points.** Le thème stoïcien est une esthétique et
   un cadre mental, pas un système de récompenses à la Habitica — dont les effets
   s'épuisent une fois la nouveauté passée.

---

## 3. Structure

**Accueil** — citation du jour (stoïciens, Bible, développement personnel, plus les
tiennes), rappels du jour, puis 9 lignes : Matin, Midi, Soir, Calendrier, Stat,
Objectifs, Idées en vrac, Outils, Réglages.

Devant Matin/Midi/Soir, une **phalange de lances** : une par ligne suivie.
Verte = faite, rouge = ratée, grise = en cours.

**Matin / Midi / Soir** — Habits, Repas (midi et soir), Choses à faire, et le soir
en plus : Bad Habit (replié) et le bilan écrit.

**Calendrier** — trois vues : Jour (tranches horaires + habits en pastilles
cliquables), Semaine, Mois. Double appui sur une journée pour l'ouvrir.

**Stat** — organisées **par famille**, repliées. Chaque famille a son score, ses
habits dessous avec une bande de carrés couvrant le mois. Clic sur une ligne →
heatmap navigable, mois en cours au centre.

**Objectifs** — deux anneaux (% du jour, série), le barème, le mois au jour le jour,
les récompenses, les écarts, les punitions, les objectifs généraux.

**Idées en vrac** — capture libre, convertible en chose à faire ou en événement.

**Outils** — suivi de poids, proverbes, et six fiches mentales : Image d'avenir,
Pot à cookie, Règle des 40 %, Rapport après action, Miroir des responsabilités,
Déclencheur · Émotion · Action. Plus les outils que tu crées.

**Réglages** — Rappels, Sauvegarde, Pause générale, Familles, Repartir à zéro,
Zone rouge, Installation.

---

## 4. Les règles, et pourquoi

### Les trois états
Une case se coche en trois temps : **gris → vert → rouge → gris**.
*Pourquoi* : cocher automatiquement en rouge ce qui n'est pas fait fausse tout,
parce qu'on n'a pas encore atteint le moment de la journée. Seul ce que tu
tranches compte.

### Un jour passé non tranché vaut rouge
Dès que la journée est écoulée, une case restée grise devient rouge partout.
*Pourquoi* : sinon on améliore son score en ne décidant pas.

### Le score du jour part de 0 %
Sur la journée en cours, **tout ce qui est prévu compte au dénominateur**, y
compris les cases encore grises. On démarre donc à 0 % le matin et on progresse.
*Pourquoi* : auparavant seul le tranché comptait, ce qui donnait 100 % dès la
première case cochée — un chiffre qui ne voulait rien dire. Le palier affiché
suit, Décrochage compris : c'est assumé, il ne se lit que le soir en ouvrant
Objectifs, jamais au réveil. Les journées closes, les stats, la série et
l'historique ne changent pas. Le jour en cours n'est jamais colorié dans les
grilles mensuelles.

### Bad Habit : on coche quand on n'a PAS cédé
Contre-intuitif mais assumé. Une seule lance pour tout le bloc, verte seulement
si tout est coché. Le bloc est replié par défaut : c'est privé.

### Le barème
| Palier | Seuil | Couleur |
|---|---|---|
| Boss | ≥ 80 % | or |
| Régulier | ≥ 70 % | argent |
| Novice | ≥ 60 % | bronze |
| Décrochage | < 60 % | rouge |

Les trois premiers comptent **tous** dans la série : seule la couleur change.
*Pourquoi* : un seuil réglable punissait la progression — viser 80 % rendait la
série plus dure à tenir. Ici, monter de palier est une reconnaissance.

**Les métaux sont réservés à Objectifs.** Partout ailleurs : vert, rouge, gris.
Le vert ne veut dire qu'une chose dans l'appli : « c'est fait ».

### Les écarts
**Un écart = une journée**, pas une ligne. Une journée compte si tu y as noté un
CHEAT ou laissé un Bad Habit non tenu.
*Pourquoi* : compter par ligne produisait 6 écarts pour 3 journées avec 2 Bad
Habits suivis — le système punissait dix fois plus vite qu'il ne récompensait.
Une journée sans aucune saisie ne compte pas.

### Récompenses et punitions
- **7 jours de série** → un point récompense
- **3 écarts sur 15 jours glissants** → un point punition, à exécuter en 5 jours
- **15 jours sans le moindre écart** → une récompense d'exception, tirée d'une
  liste cachée, qui surgit sans qu'on la choisisse

Un point ne s'applique pas tout seul : tu choisis la ligne dans le catalogue,
et tu peux revenir sur ton choix.
**Les punitions s'empilent**, jusqu'à 3 en attente. *Pourquoi* : si le compteur
se figeait pendant qu'une dette traîne, la période deviendrait une fenêtre de
gratuité — « c'est déjà foutu pour cette semaine ». Ici chaque écart continue de
coûter. Au-delà de 3, on arrête d'empiler, mais rien n'est perdu : dès qu'une
punition est réglée, la suivante prend sa place. Les punitions sont **toujours des actions**
qui font progresser, jamais des privations.

### Pas de blocage
Une dette en retard remplace la citation du jour par une pique, mais ne verrouille
jamais l'application. *Pourquoi* : le jour où tu es en retard, tu cesserais
d'ouvrir l'appli — et tu perdrais le suivi en plus de la dette.

### La pause
Individuelle (par ligne) ou générale (mode vacances). Suspend les rappels,
neutralise les jours dans les stats (carrés dorés hachurés). La série repart de
zéro au retour, **sans être comptée comme un échec** — le record historique est
conservé. C'est un nouveau chapitre, pas une défaite.

### Repartir à zéro
Assistant en trois écrans avec retour possible à chaque étape.
Par défaut : les compteurs repartent d'aujourd'hui, **rien n'est effacé**.
En option : suppression de l'historique, tout ou sur une période — cases cochées,
cheats, bilans, repas, pauses. Habits, familles, agenda, objectifs, outils et
catalogues survivent toujours.

### Dépenses
Outils → Dépenses. Description, montant, famille, date. Anneau avec bascule
Aujourd'hui / Ce mois, parts par famille autour et total au centre, plus la
moyenne par jour et la projection de fin de mois. Familles créables, renommables,
supprimables — neuf fournies par défaut dont **CHEAT**.
*Pourquoi une famille CHEAT* : elle donne le coût financier des écarts sans
qu'aucun chiffre ne circule entre les deux systèmes. Les stats de discipline
restent des stats de discipline. Un écart ne coûte pas qu'une case rouge.
Sur l'accueil, entre les rappels et la ligne Matin : le total du jour et un
bouton + . La ligne reste discrète tant que rien n'est dépensé.

### Le bouton « Ça monte »
Gros bouton rouge fixe en bas de l'accueil. Il ouvre un **routeur vers quatre
protocoles**, chacun avec sa mécanique :

| | Ça chauffe | Ça creuse | Ça tire | Ça tourne |
|---|---|---|---|---|
| pour | colère, tension | manger, boire | pulsion, scroll | ruminations |
| entrée | — | Fatigue/Tension/Ennui/FDJ | — | — |
| protocole | souffle 4/6 | eau + sortir | effort + compteur | ancrage 5-4-3 |
| durée | 60 s (6 cycles) | 4 min | 3 min | déroulé libre |
| timer visible | oui | oui | oui | non |
| relance | +60 s | non | oui | oui |
| champ texte | non | non | non | optionnel |

**Règles non négociables** du module :
1. **Aucune pénalité.** Rien de ce module n'entre dans les écarts, les séries,
   les punitions ou le score. C'est un outil d'observation, pas un item noté.
2. Aucun mot de jugement dans l'interface, sauf « J'ai craqué » explicitement
   conservé à la demande de Mrik sur l'écran de sortie de *Ça chauffe*.
3. Aucun message négatif quand un compteur retombe à zéro.
4. Sortie possible à tout moment, loggée `abandon`, sans confirmation.
5. **Discrétion totale** : écran sombre, aucun son, aucune vibration, aucune
   notification. Utilisable en public.

*Ça tire* affiche un compteur de jours depuis la dernière activation. Le nombre
de pompes et la durée de gainage se règlent dans Réglages → Ça monte.

**J'annonce** (cinquième entrée du routeur) : plafond de verres décidé à froid,
0 à 3, rappelé factuellement dans *Ça creuse*. Aucun blocage si dépassé. Un
bouton +1 verre incrémente le compteur.

**Récap** dans Outils → *Ça monte · récap* : déclenchements par type sur 7 jours,
taux de passage, répartition par créneau de 2 h — la vue la plus importante —,
causes de *Ça creuse*, jours propres, pensées notées. Aucune interprétation
automatique, aucun message de coaching. Les chiffres, rien d'autre.

### Suivi de poids
Points bruts en gris + **tendance sur 7 relevés** en vert. C'est la ligne verte
qui compte : les variations quotidiennes sont de l'eau et du sel, pas de la graisse.
Alerte au-delà de 1,2 kg/semaine, confirmation demandée si la cible passe sous
un IMC de 18,5.

---

## 5. Limites connues

- **Les rappels ne partent que si l'appli est ouverte.** Un vrai rappel programmé
  exige une app native ou un serveur. Solution prévue : un fichier d'agenda à
  importer dans Google Agenda, ou la synchronisation Google Agenda.
- **Aucune synchronisation entre appareils.** Chaque appareil a ses données.
  Passer par Réglages → Exporter / Restaurer.
- **Sauvegarde manuelle.** À faire une fois par semaine. L'accueil alerte au bout de 30 jours sans export, ou dès 3 journées enregistrées si aucune sauvegarde n'existe. Fichier
  `SurH40-sauvegarde-JJMMAAAA.json` dans les Téléchargements, jamais écrasé.

## 6. Google Agenda

Branché en **lecture seule** depuis la 4.4. Réglages → Google Agenda → Connecter.
Les événements Google apparaissent en bleu avec un badge G dans les trois vues,
ne sont jamais modifiables depuis SurH40, et peuvent être masqués d'une bascule.
Fenêtre chargée : 45 jours en arrière, 120 en avant. Resynchronisation
automatique à la réouverture de l'appli si la dernière date de plus de 30 minutes.

Identifiant OAuth (public) : projet Google Cloud `SurH40`, client `SurH40 web`,
origine autorisée `https://chaussy91.github.io`. L'application reste en mode
« Test » : seul le compte déclaré en utilisateur test peut se connecter, et Google
affiche un avertissement « application non validée » qu'il faut contourner par
« Paramètres avancés » → « Continuer ». Un client OAuth inutilisé pendant six mois
est supprimé par Google.

## 7. Chantiers ouverts

- Écriture des événements SurH40 vers Google Agenda
- Rappels fiables via fichier d'agenda
- Synchronisation multi-appareils (Supabase, gratuit)

---

## 8. Méthode de travail

Chaque version est validée par une suite de tests automatisés qui simule un vrai
parcours dans l'appli — 561 vérifications à ce jour. Toute demande est **cadrée
avant d'être codée** : on discute, tu valides, je code.
