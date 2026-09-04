# Agents, par ordre de construction

Huit agents identifies. Trois a construire maintenant. L'ordre compte plus que la liste.

## Pourquoi les deux agents que vous demandez arrivent en position 3 et 4

Vous voulez un agent qui remonte les personnes interessees par le couple des
actuateurs, et un agent qui remonte les personnes liees a la data et a la
souverainete. Ce sont les bons agents. Ils ne peuvent pas tourner en l'etat, pour deux
raisons mesurees dans la cartographie.

**Ils n'ont nulle part ou ecrire.** Un detecteur produit une ligne : *cette personne,
cette organisation, ce besoin, cette date, cette action*. Aujourd'hui cette ligne
irait dans un des quatre registres concurrents, donc nulle part. Le signal se
perdrait exactement comme il se perd deja.

**Ils travaillent dans un bruit de 76 %.** Sur une boite a 191 772 non lus sans un
seul label metier, un detecteur passe son temps a ecarter Morning Brew et le Journal
du Net. Il produira des faux positifs et vous cesserez de le lire au bout de deux
semaines.

Le registre et le triage ne sont pas des prerequis techniques. Ce sont les deux
briques qui rendent les deux autres credibles.

---

## P0. Registre unique de signaux

**Le probleme.** Quatre registres concurrents, aucun qui fasse autorite. Le CRM
HubSpot est fige depuis le 20 juin. Les contacts du Robotics Summit dorment dans une
page Notion depuis mai. La liste OPPORTUNITES d'Antoine vit dans un fil Google Chat.

**Ce que fait l'agent.** Il tient une seule base, et il est le seul a y ecrire. Un
signal, c'est six champs.

| Champ | Exemple |
|---|---|
| Personne | Jeff Waterstrode |
| Organisation | BorgWarner |
| Projet | General Robotics |
| Signal | division drivetrain en reconversion, cherche de nouvelles lignes produit |
| Source | Granola, reunion du 26 aout |
| Prochaine action | Pitch Day 29 sept. Auburn Hills, confirmer la presence |

**Ou.** Une base Notion, pas HubSpot. HubSpot a deja echoue une fois ici, et Notion
est l'outil que vous ouvrez tous les jours. HubSpot redeviendra pertinent quand une
equipe commerciale devra y lire.

**Amorcage.** Reprendre les quatre registres existants et les fusionner dans la base,
en gardant la source de chaque ligne. C'est un travail unique, une heure.

**Effort.** Une base Notion, une skill d'ecriture. Une demi-journee.

---

## P1. Triage de l'inbox

**Le probleme.** 191 772 non lus, zero label metier, 76 % de bruit sur les recherches
metier. La reponse d'Olivier Moatti chez Abenex, si elle arrive, tombera dans ce tas.

**Ce que fait l'agent.** Il passe une fois par jour sur les messages recus depuis la
veille et applique un label parmi cinq : `GR`, `Bodic`, `Argo`, `Perso`, `Veille`. Il
ne lit rien, il ne repond a rien, il ne supprime rien. Il classe.

Un message est un signal, pas de la veille, s'il repond a trois criteres.

1. L'expediteur est une personne, pas une plateforme
2. Il vous ecrit, pas a une liste de diffusion
3. Il repond a quelque chose que vous avez envoye, ou il vous cite

Les notifications LinkedIn de type *votre page a N nouveaux visiteurs* sont une
exception explicite : elles sont classees en signal, pas en veille.

**Effort.** Une skill plus une routine quotidienne. Une demi-journee.

**Gain immediat.** Les 43 visiteurs de la page General Robotics du 27 aout auraient
ete remontes le jour meme.

---

## P2. Signaux General Robotics

**C'est l'agent que vous demandez.** Specification complete dans
`skills/signaux-gr/SKILL.md`.

Il cherche le vocabulaire d'un acheteur d'actuateurs, pas le vocabulaire du secteur.
Un article sur les robots humanoides n'est pas un signal. Une phrase qui contient
*couple continu*, *backdrivability*, *rapport de reduction* ou *fenetre d'integration*
en est un, parce que seul quelqu'un qui specifie une machine ecrit ces mots.

Sources : Gmail filtre par P1, Granola, notifications LinkedIn de page, contacts
d'evenements.

Sortie : des lignes dans le registre P0, plus un digest hebdomadaire.

---

## P3. Signaux Bodic

**C'est le second agent que vous demandez.** Specification complete dans
`skills/signaux-bodic/SKILL.md`.

Il cherche trois familles de signal, et la troisieme est celle que vous sous-exploitez.

1. **Souverainete declaree.** Quelqu'un qui parle d'hebergement EU, de RGPD, de
   Cloud de confiance, de dependance a un hyperscaler.
2. **Douleur data.** Consolidation de portefeuille, reporting LP, homogeneisation
   d'ERP entre participations, due diligence.
3. **Evenement de cycle de vie.** Levee de fonds, nouveau fonds, acquisition en cours,
   preparation de sortie, changement de DSI. Antoine Bosc a dit *on essaye en ce
   moment de faire des acquisitions en Europe*. C'est un signal de cycle de vie, et il
   vaut plus que n'importe quelle mention de souverainete.

---

## P4 a P7, plus tard

### P4. Source unique de verite sur les specs RS

Le brand book dit 180 Nm pour le RS90. La reunion du 4 septembre dit 110 a 120 Nm.
Universal Robots attend les specs finalisees pour avancer.

Un agent ne resoudra pas cet ecart, vous devez trancher. Mais une fois tranche, une
fiche unique par reference, alimentee par vous et lue par tout le reste, empeche
l'ecart de revenir. C'est le prerequis de toute reponse technique a un acheteur.

**A faire avant le Pitch Day BorgWarner du 29 septembre.**

### P5. Relances

Deux fils ouverts sans relance programmee : Olivier Moatti chez Abenex depuis le 31
aout, Antoine Bosc chez Aventa depuis le 4 septembre. L'agent lit le registre P0,
repere les lignes sans mouvement depuis N jours, et propose un brouillon. Il ne
l'envoie pas.

### P6. Veille souverainete transformee en argumentaire

Vous recevez deja tout : Journal du Net sur la souverainete IA et sur ChapsVision,
l'accord Macron / Merz avec Mistral, le partenariat SAP / Scaleway. Aujourd'hui c'est
du bruit. Un agent qui transforme chaque item en une phrase utilisable devant un GP
change la nature de la source.

L'etude BCG citee par Nicolas, un ERP fragmente qui coute 20 a 30 % du prix de sortie,
est le meilleur argument commercial de Bodic. Il vit dans une transcription Granola.

### P7. Preparation d'evenement

Deux echeances : Pitch Day BorgWarner le 29 septembre, SIA 2e edition fin novembre au
Village by Crédit Agricole. L'agent prepare la liste de cibles depuis le registre,
produit les fiches, et surtout capture le retour dans le registre le soir meme. Le
Robotics Summit de mai 2026 a produit des contacts qui dorment depuis quatre mois.

---

## Ce que je ne recommande pas

**Un agent qui repond a votre place.** Ni sur email, ni sur LinkedIn. Votre valeur
dans ces echanges est la credibilite d'un ingenieur qui a livre du materiel. Un
brouillon, oui. Un envoi, non.

**Un agent qui note ou score les leads.** Vous avez seize contacts dans le CRM et cinq
reunions par mois. Le scoring se justifie a partir de quelques centaines de signaux.
Avant, il ajoute une couche d'opacite sur un volume que vous lisez en dix minutes.

**Brancher les detecteurs sur HubSpot maintenant.** HubSpot est mort depuis onze
semaines. Y ecrire automatiquement ne le ressuscite pas, ca cree un cinquieme registre.

---

## Sequence proposee

| Semaine | Livrable |
|---|---|
| 1 | Registre P0 en Notion, amorce avec les quatre registres existants |
| 1 | Triage P1, cinq labels, routine quotidienne |
| 2 | Fiche specs RS90 tranchee, avant le Pitch Day du 29 sept. |
| 2 | Agent signaux GR, branche sur le registre |
| 3 | Agent signaux Bodic, branche sur le registre |
| 4 | Relances, puis preparation SIA |
