# Protocole d'exploration multi-sources

Un protocole rejouable qui balaie toutes les sources de Rémi Haget, en extrait les
signaux commerciaux, et dit ou un agent ferait gagner du temps.

Premiere execution : 4 septembre 2026. Resultats dans `01-cartographie-2026-09.md`.

## A quoi ca sert

Trois questions, dans cet ordre.

1. Ou sont mes donnees, et lesquelles sont mortes ?
2. Quels signaux d'achat sont passes a la trappe le mois dernier ?
3. Quel agent recupere ces signaux automatiquement la prochaine fois ?

La troisieme question n'a de reponse que si les deux premieres en ont une. Un agent
de detection de signaux sans registre ou ecrire le signal ne sert a rien.

## Les six passes

Chaque passe produit un bloc de notes. Le protocole complet prend environ 40 minutes
de temps machine. A relancer tous les mois, ou avant un point strategique.

### Passe 1 : identites et perimetres

Etablir qui vous etes dans chaque outil avant de chercher quoi que ce soit. Les
signaux arrivent sur plusieurs adresses et se perdent entre elles.

| Outil | Appel | Ce qu'on cherche |
|---|---|---|
| Microsoft 365 | `get_me` | adresse pro principale |
| HubSpot | `get_organization_details` | portail, date de creation, devise |
| Gmail | `list_labels` | volume de l'inbox, taxonomie existante |
| Granola | `get_account_info` | perimetre des notes accessibles |

Sortie attendue : la liste des adresses et des espaces, avec pour chacun le projet
qu'il sert. Une adresse qui sert deux projets est un point de perte.

### Passe 2 : structure documentaire

Cartographier Notion et Drive sans lire le contenu. On veut l'arborescence et les
dates de derniere edition, pas le detail.

- Notion : `notion-search` sur chaque nom de projet, puis `notion-list-recent-pages`
- Drive : `search_files` avec `modifiedTime > <il y a 90 jours>`

Sortie attendue : un tableau espace / derniere edition / statut. Tout espace non
touche depuis 60 jours est signale comme dormant.

### Passe 3 : conversations et transcriptions

C'est la que sont les signaux les plus riches et les moins exploites.

- Granola : `list_meetings` sur 30 jours, puis `query_granola_meetings` avec la
  question metier, pas une requete par mots-cles
- Google Chat, Slack, Teams : recherche sur les noms des interlocuteurs cles

La bonne requete Granola ressemble a : *quels signaux d'interet client, quels besoins
exprimes, qui et sur quoi*. Pas : *cherche BorgWarner*.

Sortie attendue : une liste personne / organisation / besoin exprime / date / etat du
suivi. La colonne etat du suivi est celle qui fait mal.

### Passe 4 : email

L'email se traite en dernier et par requetes ciblees, jamais en parcours d'inbox.

Trois familles de requetes par projet :

1. **Vocabulaire produit.** Les termes techniques que seul un acheteur emploie.
2. **Fils actifs.** `in:sent newer_than:90d` croise avec les domaines cibles, pour
   voir ce que vous avez lance et qui n'a pas repondu.
3. **Signaux passifs.** Notifications LinkedIn, invitations, partages Drive. Ce sont
   des signaux d'interet entrants, et ils sont systematiquement noyes.

Sortie attendue : les fils ouverts sans relance, et les signaux passifs ignores.

### Passe 5 : CRM et registres de contacts

Compter, pas lire. Un CRM se juge sur deux chiffres : le nombre d'objets, et la date
de derniere modification. Si la derniere modification est anterieure a la derniere
reunion commerciale, le CRM est mort et les contacts vivent ailleurs.

Chercher ensuite les registres paralleles : fichiers `.xlsx` de contacts, pages Notion
de type liste de participants, exports d'evenements.

Sortie attendue : le nombre de registres concurrents. Au dela de un, c'est un probleme.

### Passe 6 : synthese et arbitrage

Pour chaque perte de signal identifiee, repondre a trois questions.

1. **Frequence.** Combien de fois par mois ?
2. **Cout.** Qu'est-ce qui se perd concretement ?
3. **Prerequis.** Quelle brique doit exister avant qu'un agent puisse aider ?

Un agent ne se justifie que si la frequence est mensuelle ou plus, et que le
prerequis est deja en place. Sinon on construit le prerequis d'abord.

## Regle d'arbitrage

Trois agents qui tournent valent mieux que neuf agents specifies. L'ordre de
construction suit toujours la meme logique.

1. Un endroit ou ecrire le signal (le registre)
2. Un filtre qui reduit le bruit a la source (le triage)
3. Les detecteurs metier

Les detecteurs arrivent en dernier. C'est contre-intuitif, parce que ce sont les seuls
qui ont l'air utiles.

## Sortie du protocole

Trois fichiers.

- `01-cartographie-<AAAA-MM>.md` : l'etat des sources
- `02-agents.md` : les agents, classes par ordre de construction
- `skills/<nom>/SKILL.md` : les agents prets a installer
