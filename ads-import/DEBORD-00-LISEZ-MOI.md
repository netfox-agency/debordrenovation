# Lancement Google Ads · Debord Rénovation

Compte : **393-087-6448** · EUR · Europe/Paris · facturation **APPROUVÉE**
(profil « Entreprises Debord », c'est bien le client qui paie).

Budget : **10 €/jour au départ** (~300 €/mois), montée prévue à **15-20 €/jour
vers le 10e jour**. Objectif de la phase 1 : prouver au client que les annonces
ramènent des demandes. On privilégie donc le **volume de demandes**, pas la
taille des chantiers.

---

## Structure retenue

**Une campagne, un groupe, une annonce.** `Search_Fuite-Urgence_Sud-Ardeche`

| | |
|---|---|
| Budget | **10 €/jour**, montée à 15-20 € vers le 10e jour |
| Enchères | **Maximiser les clics**, plafond 2,50 € |
| Groupe | Reparation-Fuite-Urgence, **34 mots-clés** |
| Annonce | 1 responsive, 15 titres, 4 descriptions |
| Page | `reparation-fuite-toiture-ardeche` |
| Zone | rayon 30 km autour de Lavilledieu, ciblage Présence |

**Pourquoi la fuite et rien d'autre.** À 10 €/jour, tout diviser c'est tout
affaiblir. Le seul fait solidement établi est celui-ci : les épisodes cévenols
vont de septembre à novembre, l'Ardèche est en plein dedans, plus de 200 mm de
pluie en 24 heures. **Septembre à novembre, c'est la saison des fuites.**

C'est aussi le thème dont l'intention est la plus forte : quelqu'un qui a une
fuite active appelle dans l'heure. Quelqu'un qui cherche un démoussage compare
trois devis et décide dans trois semaines. Pour prouver au client que les
annonces ramènent des demandes, c'est le chemin le plus court.

**Ce que je n'ai pas pu vérifier.** Les volumes de recherche réels de sa zone :
l'API refuse (jeton en accès explorer, le Planificateur exige basic). Le choix
repose donc sur la saisonnalité vérifiée et sur l'intention, pas sur des
volumes mesurés. Le Planificateur de mots-clés, dans ton interface, les donne
en deux minutes et permettrait de confirmer.

**En attente** (`DEBORD-06-phase2-en-attente.csv`, 61 mots-clés) : démoussage,
hydrofuge, rénovation, zinguerie, étanchéité. Ces services restent couverts en
référencement naturel, leurs pages sont indexées.

---

## Deja fait, ne pas refaire

Ces elements existent deja dans le compte, verifies par l'API. **Les recreer
ferait des doublons et fausserait le comptage des conversions.**

| Element | Etat |
|---|---|
| Demande de devis (site) | id 7747411850, ENABLED, principale, 120 EUR |
| Appel depuis le site | id 7747411853, ENABLED, principale, 120 EUR |
| Suivi sur le site | AW-18401325712 pose dans `assets/script.js` |
| Extension d'appel 06 66 14 37 84 | posee au niveau du COMPTE |
| 4 accroches | posees au niveau du COMPTE |
| Conteneur GTM-K4LHC78V | installe sur les 37 pages |

Les extensions etant au niveau du compte, elles s'appliqueront
**automatiquement** a la campagne des l'import. Rien a refaire.

**Ne cree aucune balise de conversion Google Ads dans GTM** : les conversions
partent en direct depuis le site. Une balise GTM les compterait une deuxieme
fois.

---

## Ordre de lancement

### 1. Tester le formulaire (a faire EN PREMIER)

C'est la seule inconnue qui reste, et la plus grave. Va sur
`renovation-ardeche.fr/reparation-fuite-toiture-ardeche`, remplis le
formulaire de rappel, envoie.

Deux choses a verifier :
- le mail arrive bien chez Debord ;
- la conversion « Demande de devis (site) » remonte dans Google Ads
  (comptage sous 3 a 24 h).

Si le mail n'arrive pas, **n'active rien** : 100 % des demandes seraient
perdues, quelle que soit la qualite des annonces.

### 2. Importer

Developper -> Importations -> Charger un fichier ->
**`IMPORT-GOOGLE-ADS-DEBORD.csv`** -> Apercu -> Appliquer.

La campagne arrive **en pause**, c'est voulu.

### 3. Les quatre reglages que le CSV ne peut pas porter

A faire sur la campagne, **avant d'activer**.

**a) Plafond d'enchere au CPC : 2,50 EUR**
Parametres -> Encheres -> « Definir une limite d'enchere au CPC max ».
**C'est le reglage le plus important.** En « Maximiser les clics » sans
plafond, Google ignore les encheres de groupe et peut monter a 8-12 EUR le
clic : les 10 EUR/jour acheteraient 1 clic au lieu de 5.

**b) Zone : rayon de 30 km autour de Lavilledieu**
Parametres -> Zones geographiques -> Rayon -> **44.575745, 4.453406** -> 30 km.
Supprimer « France » s'il apparait.

30 km couvre 12 communes et environ 105 400 habitants en centres urbains, de
Villeneuve-de-Berg (4 km) a Montelimar (24 km), Bourg-Saint-Andeol (27 km) et
Pierrelatte (29 km). A 25 km, Montelimar (23,6 km, la moitie du marche) aurait
ses faubourgs hors zone. A 100 km, on n'ajouterait que Valence, Ales, Orange et
Le Puy : 62 % de population en plus mais a 53-69 km, dans les marches les plus
chers.

**c) Reseaux : decocher le Reseau Display ET les partenaires de recherche**
Parametres -> Reseaux. Le fichier d'import ne porte pas ce reglage, donc Google
applique ses defauts, Display inclus.

**C'est le piege classique du budget depense sans demande.** Le Display diffuse
des bannieres sur des sites tiers : des clics a 0,20 EUR en masse, une intention
quasi nulle, et 10 EUR vides avant midi sans un seul appel.

**d) Ciblage : « Presence » et non « Presence ou interet »**
Parametres -> Zones geographiques -> Options -> **Presence**. Sinon on paie pour
des Parisiens qui lisent un article sur l'Ardeche.

### 4. Mots-cles negatifs

74 termes dans `DEBORD-05-mots-cles-negatifs.txt`. A coller en **expression**
dans Mots-cles -> Negatifs -> niveau campagne.

### 5. Activer

Passer la campagne en « Activee ». **Ne rien toucher pendant 10 jours** :
l'algorithme a besoin de donnees stables.

### 6. Le consentement aux cookies

Le suivi est actif, donc gtag depose des cookies. Une banniere avec Consent
Mode v2 est desormais necessaire : exposition CNIL, et donnees de conversion
degradees cote Google sans elle. A traiter dans les jours qui suivent le
lancement.

### 7. Au 10e jour : le seul controle qui compte

Regarder les **conversions**, pas les clics.

| Ce qu'on observe | Ce qu'on fait |
|---|---|
| Des demandes arrivent, le budget se depense | Monter a 15-20 EUR, puis rouvrir la renovation |
| Le budget ne se depense pas | Elargir le rayon a 40 km, puis rouvrir le demoussage |
| Beaucoup de clics, zero demande | Ne pas toucher aux encheres : le probleme est sur la page ou le formulaire |
| Des demandes hors zone ou hors sujet | Lire le rapport sur les termes de recherche et ajouter des negatifs |

**Obtenir les vrais volumes de recherche.** Je n'y ai pas acces par l'API (jeton
en acces « explorer », le Planificateur exige « basic »). Toi oui : Outils ->
Planification -> **Planificateur de mots-cles** -> « Decouvrir de nouveaux
mots-cles » -> « fuite toiture », « demoussage toiture », « renovation toiture »
-> cibler l'Ardeche -> colonne **tendance sur 12 mois**. Envoie-la-moi et
j'ajuste.

---

## Projection

À 10 €/jour avec un plafond à 2,50 € et un CPC moyen attendu autour de 1,90 €
sur les deux thèmes retenus : environ **5,3 clics par jour**, soit **160 clics
par mois**.

| Taux de conversion | Demandes/mois | Coût par demande |
|---|---:|---:|
| 5 % | 8 | 38 € |
| 8 % | 13 | 23 € |
| 12 % | 19 | 16 € |

À 20 €/jour, ces chiffres doublent : 16 à 38 demandes par mois.

Pour des chantiers à 2 000-15 000 €, une demande à 23 € reste très rentable si
Debord signe un devis sur quatre.

---

## Quand passer en « Maximiser les conversions »

Rester en **Maximiser les clics** au démarrage : c'est le bon choix tant qu'il
n'y a aucun historique de conversion, et c'est ce qui alimente l'algorithme le
plus vite.

Basculer quand la campagne a accumulé **au moins 30 conversions sur 30 jours**.
Au rythme projeté, c'est réaliste vers le **2e ou 3e mois**. Basculer trop tôt
étrangle la diffusion : l'algorithme n'a pas assez de signal et arrête de
dépenser.

---

## Ce qui reste bloquant

1. **Le formulaire n'a jamais été testé de bout en bout.** Si Web3Forms ne
   délivre pas, 100 % des demandes sont perdues. Trente secondes depuis un
   navigateur, à faire avant le premier euro dépensé.
2. **Identifiant de conversion AW manquant** (étape 1 ci-dessus).
3. **3 avis Google seulement.** C'est le levier de conversion le plus fort et le
   seul gratuit.
