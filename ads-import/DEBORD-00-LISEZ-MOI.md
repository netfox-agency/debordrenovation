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

### 3. Les quatre réglages que le CSV ne peut pas porter

À faire à la main dans l'interface, sur la campagne, **avant d'activer**.

**a) Plafond d'enchère au CPC : 2,50 €**
Paramètres → Enchères → « Définir une limite d'enchère au CPC max ».
**C'est le réglage le plus important.** En « Maximiser les clics » sans plafond,
Google ignore les enchères de groupe et peut monter à 8-12 € le clic : les 400 €
achèteraient environ 25 clics au lieu de 125.

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

**c) Réseaux : décocher le Réseau Display ET les partenaires de recherche**
Paramètres → Réseaux. Le fichier d'import ne porte pas ce réglage, donc Google
applique ses valeurs par défaut, qui incluent le Display.

**C'est le piège classique du budget dépensé sans demande.** Le Réseau Display
diffuse des bannières sur des sites tiers : des clics à 0,20 € en masse, une
intention quasi nulle, et un budget quotidien vidé avant midi sans un seul
appel. Sur une campagne Search à 13 €/jour, il peut absorber la majorité des
dépenses. Les partenaires de recherche sont moins nocifs mais à surveiller :
à rouvrir plus tard seulement si le Search pur ne consomme pas le budget.

**d) Ciblage : « Présence » et non « Présence ou intérêt »**
Paramètres → Zones géographiques → Options → **Présence : personnes se trouvant
dans les zones ciblées**. Sinon on paie pour des Parisiens qui lisent un article
sur l'Ardèche.

### 4. Consentement aux cookies

Aujourd'hui le site ne pose aucun cookie de suivi : les balises sont en
attente d'identifiant. **Dès qu'on activera le suivi de conversion**, gtag
déposera des cookies et il faudra une bannière de consentement avec Consent
Mode v2. Sans elle : exposition CNIL, et données de conversion dégradées côté
Google pour les visiteurs européens. À prévoir en même temps que l'étape 1.

### 5. Mots-clés négatifs

74 termes dans `DEBORD-05-mots-cles-negatifs.txt` : emploi, formation,
bricolage, matériaux, etc. À coller en **expression exacte** dans
Mots-clés → Négatifs → au niveau campagne.

### 6. Extensions

Avant d'activer, ajouter au minimum :
- **Extension d'appel** avec le 06 66 14 37 84 : c'est le levier le plus rapide,
  le prospect appelle depuis Google sans même visiter le site.
- **Liens annexes** vers les autres prestations du site.
- **Accroches** : Devis gratuit · Déplacement gratuit · Garantie décennale ·
  Artisan local.

### 7. Activer

Passer la campagne en « Activée ». Ne rien toucher pendant **10 jours** :
l'algorithme a besoin de données stables.

### 8. Au 10e jour : le seul contrôle qui compte

Ouvrir le rapport par **groupe d'annonces**, et regarder les **conversions**,
pas les clics.

| Ce qu'on observe | Ce qu'on fait |
|---|---|
| Le démoussage capte le budget mais convertit moins | Sortir Reparation-Fuite dans sa propre campagne, avec son budget dédié |
| La fuite convertit bien et le budget suit | Ne rien changer, monter le budget à 15-20 € |
| Aucun des deux ne dépense le budget | Élargir le rayon à 40 km avant toute autre chose |
| Beaucoup de clics, zéro demande | Ne pas toucher aux enchères : le problème est sur la page ou le formulaire |

**Obtenir les vrais volumes de recherche.** Je n'y ai pas accès par l'API (le
jeton du compte est en accès « explorer », le Planificateur exige « basic »).
Toi tu les as dans l'interface : Outils → Planification → **Planificateur de
mots-clés** → « Découvrir de nouveaux mots-clés » → saisir « fuite toiture »,
« demoussage toiture », « renovation toiture » → cibler l'Ardèche → puis
regarder la colonne **tendance sur 12 mois**. Ça donnera la saisonnalité réelle
de sa zone, mois par mois. Envoie-la-moi et j'ajuste la répartition.

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
