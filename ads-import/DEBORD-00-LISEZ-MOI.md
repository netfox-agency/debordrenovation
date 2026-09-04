# Lancement Google Ads · Debord Rénovation

Compte : **393-087-6448** · EUR · Europe/Paris · facturation **APPROUVÉE**
(profil « Entreprises Debord », c'est bien le client qui paie).

Budget : **400 €/mois = 13,17 €/jour**.

---

## Structure retenue

**Une seule campagne, 3 groupes d'annonces.** Avant : 4 campagnes, 9 groupes.

| Groupe | Mots-clés | Page d'atterrissage |
|---|---:|---|
| Reparation-Fuite-Urgence | 38 | reparation-fuite-toiture-ardeche |
| Demoussage-Hydrofuge | 24 | demoussage-toiture-ardeche |
| Renovation-Toiture | 17 | renovation-toiture-ardeche |

**Mis de côté pour la phase 2** (`DEBORD-06-phase2-en-attente.csv`) :
Zinguerie-Gouttiere (16 mots-clés) et Etancheite-Toit-Plat (8). Ces deux
services restent couverts en référencement naturel, leurs pages sont
indexées. On les rouvre au 2e ou 3e mois, ou si le budget augmente.

**Pourquoi une seule campagne.** Le budget est fixé au niveau de la campagne.
Avec 4 campagnes, on figeait 4 enveloppes de 3 à 4 €/jour et l'algorithme ne
pouvait pas déplacer l'argent vers ce qui marche. Avec une seule enveloppe de
13,17 €, il alimente librement les groupes qui rapportent.

**Pourquoi 3 groupes et pas 9.** Trois anciens groupes (Fuite toiture, Urgence
couvreur, Tempête) pointaient vers **la même page** : les séparer ne servait à
rien et divisait les données par trois. Démoussage et hydrofuge se vendent
ensemble et partagent la même saison.

Ce qui se fragmente vraiment avec trop de groupes, ce n'est pas l'enchère :
l'apprentissage des enchères se fait au niveau de la **campagne**, pas du
groupe. C'est l'**annonce responsive** qui souffre : chacune teste ses
combinaisons de titres séparément et a besoin de volume. À 200 clics par mois,
3 groupes donnent 66 clics chacun, 5 groupes n'en donnent que 40.

La campagne de marque est supprimée : sans notoriété, elle ne dépensera pas et
fragmente pour rien.

---

## Ordre de lancement

### 1. Créer les conversions AVANT tout

Sans elles, l'algorithme optimise à l'aveugle et on ne pourra jamais passer en
« Maximiser les conversions ».

Objectifs → Conversions → Nouvelle action → **Site Web** →
`renovation-ardeche.fr` → configuration manuelle. Créer deux actions :

| Nom | Catégorie | Valeur |
|---|---|---|
| Demande de devis | Envoi de formulaire de prospect | 120 € |
| Appel téléphonique | Appel téléphonique | 120 € |

Récupérer ensuite l'**identifiant AW-XXXXXXXXX** et les **deux libellés**, puis
me les donner : je les pose dans `assets/script.js`, où le code de suivi attend
déjà (attribution gclid, UTM, référence de demande, tout est câblé).

### 2. Importer

Développer → Importations → Charger un fichier →
**`IMPORT-GOOGLE-ADS-DEBORD.csv`** → Aperçu → Appliquer.

La campagne arrive **en pause**, c'est voulu.

### 3. Les trois réglages que le CSV ne peut pas porter

À faire à la main dans l'interface, sur la campagne, **avant d'activer**.

**a) Plafond d'enchère au CPC : 2,50 €**
Paramètres → Enchères → « Définir une limite d'enchère au CPC max ».
**C'est le réglage le plus important.** En « Maximiser les clics » sans plafond,
Google ignore les enchères de groupe et peut monter à 8-12 € le clic : les 400 €
achèteraient environ 40 clics au lieu de 240.

**b) Zone géographique : rayon de 30 km autour de Lavilledieu**
Paramètres → Zones géographiques → Rayon → coordonnées **44.575745, 4.453406**
→ 30 km. Supprimer « France » s'il apparaît.

30 km couvre 12 communes et environ 105 400 habitants en centres urbains, de
Villeneuve-de-Berg (4 km) à Montélimar (24 km), Bourg-Saint-Andéol (27 km) et
Pierrelatte (29 km).

Pourquoi pas 25 km : Montélimar est à 23,6 km et pèse 40 000 des 84 100
habitants de ce rayon, soit près de la moitié. À 25 km il ne reste que 1,4 km
de marge et ses faubourgs sortent de la zone. À 30 km, l'agglomération entière
est dedans, et on gagne Pierrelatte et Bourg-Saint-Andéol au passage.

Pourquoi pas 100 km : cela n'ajouterait que Valence, Alès, Orange et Le Puy,
62 % de population en plus mais à 53-69 km, dans les marchés les plus chers et
les plus concurrentiels. Avec 13 €/jour, le budget s'y viderait sans
déplacement rentable.

**c) Ciblage : « Présence » et non « Présence ou intérêt »**
Paramètres → Zones géographiques → Options → **Présence : personnes se trouvant
dans les zones ciblées**. Sinon on paie pour des Parisiens qui lisent un article
sur l'Ardèche.

### 4. Mots-clés négatifs

43 termes dans `DEBORD-05-mots-cles-negatifs.txt` : emploi, formation,
bricolage, matériaux, etc. À coller en **expression exacte** dans
Mots-clés → Négatifs → au niveau campagne.

### 5. Extensions

Avant d'activer, ajouter au minimum :
- **Extension d'appel** avec le 06 66 14 37 84 : c'est le levier le plus rapide,
  le prospect appelle depuis Google sans même visiter le site.
- **Liens annexes** vers les 3 pages d'atterrissage actives.
- **Accroches** : Devis gratuit · Déplacement gratuit · Garantie décennale ·
  Artisan local.

### 6. Activer

Passer la campagne en « Activée ». Ne rien toucher pendant **15 jours** :
l'algorithme a besoin de données stables.

---

## Projection

À 13,17 €/jour avec un plafond à 2,50 € et un CPC moyen attendu autour de
1,80 à 2,20 € : environ **6 à 7 clics par jour**, soit **190 à 210 clics par
mois**.

| Taux de conversion | Demandes/mois | Coût par demande |
|---|---:|---:|
| 5 % | 10 | 40 € |
| 8 % | 16 | 25 € |
| 12 % | 24 | 17 € |

Pour des chantiers à 2 000-15 000 €, une demande à 25 € reste très rentable si
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
