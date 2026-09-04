---
name: signaux-bodic
description: Detecte et qualifie les signaux d'achat pour Bodic, la plateforme data et IA souveraine pour les societes de gestion. Balaie Gmail, Granola, Google Chat et Notion pour reperer les personnes liees a la data, a la souverainete et aux fonds d'investissement, puis ecrit les signaux qualifies dans le registre. A utiliser sur "signaux Bodic", "qui parle de souverainete", "prospects fonds", "veille data souveraine", "digest Bodic", "prepare le SIA", "qui suivre chez les GP". Se declenche aussi avant un evenement de place ou un point avec Antoine Jeanjean.
---

# Signaux Bodic, data et souverainete pour les fonds

Detecter les societes de gestion qui ont un probleme de data, pas celles qui ont un
avis sur la souverainete.

## Le critere central

La souverainete est rarement le declencheur d'achat. C'est le critere de selection
final. Le declencheur est presque toujours une douleur data ou un evenement de cycle
de vie du fonds.

Consequence sur la detection : une mention de souverainete seule vaut moins qu'une
mention d'acquisition en cours. Antoine Bosc chez Aventa a ecrit *on essaye en ce
moment de faire des acquisitions en Europe*. Aucun mot de souverainete, et c'est
pourtant le meilleur signal du mois.

Regle : **classer d'abord par evenement de cycle de vie, ensuite par douleur data,
la souverainete en dernier.**

## Les trois familles de signal

### Famille A, evenement de cycle de vie, priorite haute

Ouvre une fenetre datee. C'est la famille la plus actionnable et la moins surveillee.

acquisition en cours, build-up, closing, nouveau fonds, levee d'un vehicule,
first closing, preparation de sortie, exit, cession, due diligence, changement de
DSI ou de COO, arrivee d'un head of data, integration post-acquisition,
consolidation de participations, montee en puissance d'une equipe operations

### Famille B, douleur data

Le probleme que Bodic resout. Presence d'une friction, pas d'un projet abstrait.

reporting LP, consolidation de portefeuille, homogeneisation, source unique de
verite, donnees eclatees entre participations, ERP fragmente, Oracle et SAP,
retraitement manuel, Excel, delai de production du reporting, qualite de donnee,
data room, referentiel, gouvernance de la donnee

### Famille C, souverainete declaree

Critere de selection, rarement declencheur. A retenir comme qualificatif d'une
famille A ou B, pas seul.

souverainete, souverain, hebergement EU, cloud de confiance, SecNumCloud, RGPD,
DORA, dependance hyperscaler, sortie d'AWS ou d'Azure, OVH, Scaleway, Mistral,
stack europeen, EU-compliant, extraterritorialite, Cloud Act

### Bruit a ecarter

Les newsletters qui emploient ce vocabulaire tous les jours sans jamais porter de
signal.

actualite@ga.journaldunet.com, ia@ga.journaldunet.com,
newsletters-noreply@linkedin.com, placement@news.meilleurtaux.com,
info@lesfrancais.press, newyork@frenchmorning.com, mathieubernard@substack.com

Ces sources alimentent la veille argumentaire (agent P6), jamais la detection.

## Sources, dans l'ordre

### 1. Granola

```
query_granola_meetings :
"Dans mes reunions des N derniers jours, quels interlocuteurs lies a des fonds,
societes de gestion ou grands comptes ont exprime un besoin de consolidation de
donnees, un projet d'acquisition, ou une contrainte de souverainete ? Pour chacun :
organisation, role, la phrase exacte, et l'echeance si elle est mentionnee."
```

Extraire la phrase exacte, pas un resume. Une citation d'un GP est reutilisable en
rendez-vous, un resume ne l'est pas.

### 2. Gmail

```
Reponses entrantes des prospects
  in:inbox newer_than:60d {Bodic souverainete "societe de gestion" "asset manager"
  "fonds" reporting consolidation} -from:journaldunet.com -from:linkedin.com

Fils que vous avez ouverts
  in:sent newer_than:90d {Bodic "data pour societe de gestion" souverainete}

Copies vers l'adresse Bodic
  {to:haget@bodic.fr cc:haget@bodic.fr} newer_than:90d
```

La troisieme requete est importante : les approches Bodic partent de Gmail avec
`haget@bodic.fr` en copie, donc les fils vivent dans Gmail et pas dans la boite Bodic.

Appeler `get_thread` sur tout fil retenu. Les apercus de recherche masquent les
messages recents.

### 3. Google Chat et Notion

Antoine Jeanjean transmet la liste OPPORTUNITES par Google Chat. Elle ne doit pas
rester la.

- Google Chat, fil avec ajeanjean@opt2a.com
- Notion, `BODIC - Process` puis `Sales - Info GP` et `Push-backs`
- `BODIC — Contacts consolidés par priorité (20_08_2026).xlsx`

A chaque passage, verifier que la derniere version de la liste OPPORTUNITES est
reportee dans le registre.

## Qualification

| Niveau | Definition | Action |
|---|---|---|
| **Chaud** | famille A datee, ou demande explicite de demo ou de tarif | fiche registre plus action sous 48 h |
| **Tiede** | famille B sans echeance, ou reponse positive sans suite | fiche registre, relance a 14 jours |
| **Froid** | famille C seule, interet de principe | ligne registre, a nourrir par contenu |

Le delai de relance est plus court que pour General Robotics. Un cycle de fonds se
joue sur des fenetres de quelques semaines.

## Ecriture dans le registre

```
Personne         | Antoine Bosc
Organisation     | Aventa / NextStage AM
Projet           | Bodic
Signal           | acquisitions en Europe en cours, a decouvert Bodic,
                   reponse positive du 4 sept. 2026
Source           | Gmail, fil "News & NextStage AM"
Prochaine action | relance le 18 sept., proposer un point de 30 minutes
```

## Arguments a reutiliser

Trois preuves existent deja et ne sont pas formalisees. L'agent les rappelle quand un
signal de la famille correspondante apparait.

| Signal detecte | Argument disponible | Source |
|---|---|---|
| preparation de sortie, exit | un ERP fragmente a l'exit peut couter 20 a 30 % du prix de cession, etude BCG citee par Nicolas de SAP | Granola, 28 aout 2026 |
| souverainete, dependance hyperscaler | infrastructure OVH et EU depuis plus de deux ans, en avance sur la tendance | Granola, 28 aout 2026 |
| choix concurrentiel, appel d'offres | un GP energie a retenu Bodic pour son stack data souverain | Granola, 19 aout 2026 |

Ces trois arguments vivent aujourd'hui dans des transcriptions. Ils devraient etre
dans `references/contenus.md` de la skill `bodic-doc`. Tant qu'ils n'y sont pas, ils
ne sortent pas dans un document client.

## Echeance a preparer

**SIA, 2e edition, fin novembre 2026, Village by Crédit Agricole.** Un mois avant,
l'agent produit la liste des cibles issues du registre, classees par famille de
signal. Le soir de l'evenement, il capture les retours. Les contacts du Robotics
Summit de mai 2026 dorment depuis quatre mois faute de cette etape.

## Regles de redaction

La skill `bodic-doc` s'applique a toute sortie lisible par un tiers.

- Jamais de tiret cadratin
- Une idee par ligne, phrases courtes, verbe d'action en tete
- Un seul appel a l'action par document
- Vouvoiement en premier contact
- Vocabulaire banni : leverage, robuste, scalable, optimiser, synergie,
  revolutionnaire, best-in-class, cutting-edge, solution
- Aucun chiffre client qui ne soit pas dans `references/contenus.md` ou fourni par
  Rémi. Sinon, ecrire **A completer**.
