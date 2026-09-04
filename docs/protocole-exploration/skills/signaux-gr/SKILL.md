---
name: signaux-gr
description: Detecte et qualifie les signaux d'achat pour la ligne actuateurs de General Robotics (serie RS, QDD, reducteurs, couple). Balaie Gmail, Granola, les notifications LinkedIn de page et les listes de contacts d'evenements, puis ecrit les signaux qualifies dans le registre. A utiliser sur "signaux GR", "qui s'interesse aux actuateurs", "veille couple", "prospects hardware", "digest GR", "qui a parle de nos actuateurs cette semaine", ou dans une routine hebdomadaire. Se declenche aussi avant un evenement robotique (Pitch Day, Robotics Summit, salon) pour preparer la liste de cibles.
---

# Signaux General Robotics, ligne actuateurs

Detecter les gens qui specifient une machine, pas les gens qui lisent des articles sur
la robotique.

## Le critere central

Un signal, c'est quelqu'un qui a un probleme d'integration. Pas quelqu'un qui
s'interesse au secteur.

La difference tient dans le vocabulaire. Un journaliste, un investisseur ou un
curieux ecrivent *robots humanoides*, *actuateurs de nouvelle generation*, *marche de
la robotique*. Un acheteur ecrit *couple continu*, *rapport de reduction*,
*backdrivability*, *encombrement axial*. Il donne des chiffres et des unites.

Regle : **si le message ne contient ni chiffre, ni unite, ni contrainte
d'integration, ce n'est probablement pas un signal.**

## Vocabulaire de detection

### Niveau 1, signal fort

Presence d'une specification chiffree ou d'une contrainte physique.

couple continu, couple de pointe, Nm, torque density, densite de couple,
backdrivability, retro-entrainabilite, rapport de reduction, 17:1, harmonic drive,
reducteur planetaire, cycloidal, encombrement, diametre exterieur, hauteur axiale,
inertie rotorique, temperature de fonctionnement, IP67, IP68, cycle de charge,
duty cycle, tension bus, 24 V, 48 V, EtherCAT, CAN, protocole de commande

### Niveau 2, signal de contexte

Indique un projet en cours sans specification.

fenetre d'integration, integration window, prototype, banc de test, validation des
performances, echantillon, sample, NDA, LOI, lead time, delai de livraison, prix
unitaire, volume serie, series production, bill of materials, BOM, sourcing,
second source, qualification fournisseur

### Niveau 3, evenement

Ouvre une fenetre commerciale meme sans vocabulaire technique.

levee de fonds d'un fabricant de robots, nouveau programme humanoide, recrutement
d'un hardware lead ou d'un integration engineer, changement de fournisseur
d'actuateurs, salon ou pitch day, visiteurs de la page LinkedIn

### Bruit a ecarter systematiquement

Ces expediteurs ne produisent jamais de signal. Les ecarter avant toute analyse.

crew@morningbrew.com, techbrew@morningbrew.com, dan@tldrnewsletter.com,
a16z@substack.com, noahpinion@substack.com, rideai@substack.com,
actualite@ga.journaldunet.com, ia@ga.journaldunet.com,
newsletters-noreply@linkedin.com, dailyskimm@morning7.theskimm.com

Exception : `linkedin@em.linkedin.com` quand l'objet contient *Page visitors* ou
*visiteurs de la page*. C'est un signal, pas de la veille.

## Sources, dans l'ordre

### 1. Granola

La source la plus dense. Poser une question metier, pas une requete par mots-cles.

```
query_granola_meetings :
"Dans mes reunions des N derniers jours, qui a exprime un besoin d'actuateur,
de reducteur ou de couple ? Pour chaque personne : son organisation, la
contrainte technique exprimee, et ce qui bloque aujourd'hui."
```

Extraire de la reponse : la personne, l'organisation, la contrainte, le blocage.
Le blocage est le champ le plus utile, c'est lui qui dicte l'action.

### 2. Gmail

Ne jamais parcourir l'inbox. Trois requetes ciblees.

```
Signal entrant technique
  {couple actuateur "Nm" reducteur torque backdrivability "harmonic drive"}
  -from:substack.com -from:morningbrew.com -from:journaldunet.com newer_than:30d

Fils que vous avez ouverts et qui n'ont pas repondu
  in:sent newer_than:90d {actuator RS90 RS120 QDD "General Robotics"}

Signaux passifs
  from:linkedin.com subject:{"Page visitors" "visiteurs"} newer_than:30d
```

Pour tout fil retenu, appeler `get_thread`. Les resultats de recherche ne montrent
que les messages les plus anciens, donc la reponse recente d'un prospect n'apparait
pas dans l'apercu.

### 3. Notion

Les contacts d'evenements dorment ici. Verifier a chaque passage.

- `🤝 Robotics Summit — Contacts May 2026`
- `General Robotics / Weekly Cedric`, sous-pages Sales et Competitors

Toute fiche de contact sans suivi depuis plus de 60 jours remonte comme signal
dormant, avec sa date d'origine.

## Qualification

Trois niveaux, et un seul declenche une action immediate.

| Niveau | Definition | Action |
|---|---|---|
| **Chaud** | contrainte technique chiffree, ou demande explicite de specs, ou echeance datee | fiche registre plus action sous 48 h |
| **Tiede** | projet en cours, pas de specification, pas d'echeance | fiche registre, relance a 21 jours |
| **Froid** | interet secteur, pas de projet identifie | ligne registre, pas d'action |

Un contact qui attend des specs est **chaud**, meme s'il ne relance pas. Universal
Robots est reste bloque dans cet etat sans qu'aucune action ne soit posee.

## Ecriture dans le registre

Une ligne par signal, six champs. Ne jamais ecrire deux lignes pour la meme personne :
enrichir la ligne existante et dater l'ajout.

```
Personne         | Jeff Waterstrode
Organisation     | BorgWarner
Projet           | General Robotics
Signal           | division drivetrain en reconversion post-electrification,
                   cherche de nouvelles lignes produit, frein sur le ROI court terme
Source           | Granola, reunion du 26 aout 2026
Prochaine action | Pitch Day 29 sept. Auburn Hills, confirmer la presence
```

## Digest hebdomadaire

Court. Trois sections, jamais plus d'une page.

1. **Chauds** : personne, organisation, ce qu'ils attendent, l'action a poser
2. **Nouveaux tiedes** : une ligne chacun
3. **Dormants** : signaux sans mouvement depuis 60 jours

Pas de section veille. Pas de commentaire de marche. S'il n'y a aucun signal chaud,
l'ecrire en une ligne et s'arreter.

## Regles de redaction

Le brand book General Robotics s'applique a toute sortie lisible par un tiers.

- Jamais de tiret cadratin
- Chiffres et unites colles : `180 Nm`, `24 V`, `17:1`
- Une affirmation par phrase
- Vocabulaire banni : revolutionnaire, best-in-class, cutting-edge, solution,
  scalable, robuste, optimiser, leverage

## Avertissement sur les specs

Deux valeurs de couple de pointe circulent pour le RS90 : 180 Nm dans le brand book,
110 a 120 Nm dans les transcriptions de septembre 2026.

Cet agent **ne cite jamais de valeur de couple** dans une sortie destinee a un tiers
tant que l'ecart n'est pas tranche. Il signale la demande et laisse Rémi repondre.
