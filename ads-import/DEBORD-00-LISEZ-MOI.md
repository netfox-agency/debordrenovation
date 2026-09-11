# Google Ads · Debord Rénovation · état au 11 septembre 2026

Compte **393-087-6448** · EUR · Europe/Paris · facturation approuvée
(profil « Entreprises Debord » : c'est bien le client qui paie).

> Les CSV de ce dossier ne sont plus la source de vérité. La campagne a été
> créée et modifiée **par l'API**, parce qu'un fichier d'import ne porte ni le
> plafond d'enchère, ni la coupure du Display, ni le rayon, ni le ciblage
> Présence. Les scripts sont dans `~/ads-write/debord-*.py`.

---

## Ce qui tourne

```
Search_Fuite-Urgence_Sud-Ardeche          ENABLED
├── Reparation-Fuite-Urgence   19 mots-clés  → /reparation-fuite-toiture-ardeche
└── Couvreur-Local             17 mots-clés  → une page de ville par mot-clé
```

| Réglage | Valeur |
|---|---|
| Budget | 10 €/jour |
| Enchères | Maximiser les clics, plafond **2,50 €** |
| Réseaux | Google seul · **Display et partenaires coupés** |
| Zone | rayon **50 km** sur 44.575745, 4.453406 · **Présence** |
| Négatifs | **80** en expression, niveau campagne |
| Extensions | appel 06 66 14 37 84 · 4 accroches · 4 liens annexes |
| Conversions | Demande de devis (7747411850) · Appel depuis le site (7747411853) |

---

## Ce qui s'est passé depuis le lancement, et ce que ça a appris

**J'avais construit une liste de mots-clés trop étroite.** 15 des 34 étaient en
« faible volume de recherche » et ne sortaient jamais : tous ceux qui collaient
le service et la ville (« fuite toiture aubenas »). Personne ne tape ça. Ils ont
été retirés.

**Le mot-clé le plus recherché du métier était absent** : « couvreur aubenas ».
D'où le groupe `Couvreur-Local`, avec une URL par mot-clé vers la page de la
commune, dont le titre reprend la requête mot pour mot.

**Une description contenait le numéro de téléphone**, ce que Google interdit
(`PHONE_NUMBER_IN_AD_TEXT`). L'annonce était limitée. La corriger a coûté 48 h
de diffusion, le temps de la revalidation : une annonce responsive n'est pas
modifiable, il faut la recréer.

**Le rapport des termes de recherche a révélé une fuite de budget** dès 3,61 €
dépensés : « prix bâche toiture au m2 », un acheteur de matériau, avait consommé
1,38 €. Six négatifs produit ont été ajoutés. Le piège : notre mot-clé est
« bachage » (le service), le parasite « bâche » (le produit). Les négatifs ne
prenant pas les variantes proches, bloquer l'un ne bloque pas l'autre.

**Les 12 pages de ville ont reçu le formulaire express.** Leur seul formulaire
était en bas de page, à 3 413 px sur mobile. Il est maintenant à 801-847 px,
visible sans scroller.

---

## Le suivi, semaine par semaine

### Chaque semaine : le rapport des termes de recherche

C'est le travail le plus rentable sur un compte Ads. En 4 jours il avait déjà
révélé une fuite. Le mot-clé le plus à risque est **« couvreur »** en
expression : il porte le volume, mais c'est le plus large.

### Le seul chiffre à regarder à 48 h : la dépense quotidienne

| Dépense | Diagnostic | Action |
|---|---|---|
| 8 à 10 €/jour | volume trouvé | ne rien toucher, attendre les conversions |
| moins de 3 €/jour | marché plus petit que prévu | élargir le rayon au-delà de 50 km |
| 0 impression | annonce refusée | onglet Annonces, colonne Statut |

### Au 10e jour : les conversions par groupe, pas les clics

« Maximiser les clics » achète le clic le moins cher. `Couvreur-Local` étant
moins cher que l'urgence, le budget va probablement basculer vers lui. Ce n'est
pas un défaut tant que l'objectif est le volume de demandes, mais si la fuite
convertit nettement mieux avec moins de clics, il faudra lui donner sa propre
campagne pour lui garantir son budget.

### Quand passer en « Maximiser les conversions »

À partir de **30 conversions sur 30 jours**. Basculer plus tôt étrangle la
diffusion : sans signal suffisant, l'algorithme arrête de dépenser.

---

## Ce qui reste ouvert

**Trois avis Google.** C'est désormais le premier frein, et il ne se règle pas
dans le compte Ads. À trafic égal, passer de 3 à 20 avis ferait plus pour les
demandes que n'importe quel réglage restant. Ça bloque aussi les annonces Local
Services, dont le classement repose massivement sur les avis.

**Pas de bannière de consentement.** Le suivi est actif, donc gtag dépose des
cookies. Consent Mode V2 manque : exposition CNIL, et conversions sous-comptées
pour les visiteurs qui refusent.

**Les volumes de recherche réels restent inconnus.** L'API du Planificateur est
refusée au jeton du compte (accès « explorer », il faut « basic »). Ils sont
accessibles depuis l'interface : Outils → Planification → Planificateur de
mots-clés.

**61 mots-clés en attente** (`DEBORD-06-phase2-en-attente.csv`) : démoussage,
hydrofuge, rénovation, zinguerie, étanchéité. À rouvrir quand le budget passe à
15-20 €/jour, en commençant par la rénovation.
