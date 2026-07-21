# Plan de design — Debord Rénovation (refonte renovation-ardeche.fr)

Site vitrine **one-page premium statique** (HTML/CSS/JS pur, pas de build) pour un couvreur
en Ardèche du Sud. Dossier `debord-renovation-refonte/`.

**Règle d'intégrité absolue : rien d'inventé.** Aucun faux avis, aucune note étoilée, aucun
chiffre, aucun prix, aucun label (RGE/Qualibat) qui ne soit pas sourcé du site actuel ou des
mentions légales. Les compteurs vides du site actuel (« Existe depuis », « Clients satisfaits »,
« Toits durables », « Projets complétés ») ne sont **pas** repris tant que le client n'a pas
fourni les nombres.

---

## Décisions tranchées

| # | Décision | Choix retenu |
|---|----------|--------------|
| D1 | Cible de la review | Scraper le site puis reviewer |
| D2 | Direction visuelle | Hybride — plomberie réutilisée, visuel neuf |
| D3 | Nom de marque | **« Debord Rénovation »** (contre recommandation ; user a le contexte client) |
| D4 | Élément signature | Photographie éditoriale — le comparateur avant/après est abandonné |
| D5 | Logo & nom | Logo typographique sobre + marque bloc bleu |
| **D7** | **Direction visuelle (révisée)** | **Design system de Bretonnet Net Services + hero vidéo, cartes bento photo** |

**Révision majeure (D7).** La première direction (vert cévenol, Fraunces, index typographique)
a été rejetée. Le style retenu est celui de **Bretonnet Net Services** (`bretonnet-net-services-refonte/`),
avec la vidéo `3386_Close_up_look_of_the_roofer_getting_off_the_nails` en hero. La contrainte qui
avait imposé l'index typographique (4 sujets photographiés pour 11 prestations) est levée : le
dossier `~/Downloads` contient une douzaine de photos couvreur haute résolution **inédites sur les
autres sites clients**.

**Résolution SEO du conflit D3.** Marque affichée « Debord Rénovation », mais le domaine, la FAQ et
la page services existante disent « Rénovation Ardèche ». Donc : `name: "Debord Rénovation"` +
`alternateName: "Rénovation Ardèche"` dans le balisage, et « Rénovation Ardèche » conservé comme
descripteur métier dans le logo, le `<title>` et le footer. On garde l'identité de l'artisan sans
jeter le référencement acquis.

---

## Contenu réel (100 % scrapé)

**Identité** — Marque : Debord Rénovation · Descripteur : Rénovation Ardèche · Couvreur ·
Baseline littérale : « Votre partenaire de confiance en toiture. » · Raison sociale (mentions
légales) : Rénovation Ardèche · SIRET 424 367 340 00025 · 8 Impasse Louis Lauriol, 07170
Lavilledieu · 06 66 14 37 84 · Entrepreneur individuel, artisan local implanté en Ardèche du Sud ·
Garantie décennale · Devis gratuit et sans engagement · Déplacement gratuit pour devis.

**11 prestations** (toutes sourcées) : rénovation de toiture (tuile canal, ardoise, lauze, tuile
mécanique) · réparation & détection de fuite · traitement de charpente · zinguerie · faîtage ·
étanchéité toits plats & terrasses · isolation des combles · démoussage · hydrofuge incolore ou
coloré · nettoyage & ravalement de façade · entretien préventif.

**Zone** : tout le département de l'Ardèche + communes limitrophes du Gard et de la Drôme.
17 communes citées : Aubenas, Ruoms, Vallon-Pont-d'Arc, Villeneuve-de-Berg, Bourg-Saint-Andéol,
Le Teil, Saint-Paul-le-Jeune, Largentière, Les Vans, Joyeuse, Privas, Annonay, Lamastre,
Tournon-sur-Rhône, Guilherand-Granges, Barjac, Pierrelatte.

**Cibles** : particuliers, professionnels, campings, copropriétés. **Aides** : MaPrimeRénov',
éco-PTZ, TVA 10 %, aides locales. **Durées de vie citées** : ardoise 75–100 ans · tuile canal
50–80 ans · zinc 50–80 ans · toit plat 25–40 ans. Combles non isolés = jusqu'à 30 % des pertes.

**Les 3 chiffres du hero sont sourcés, pas inventés** : 11 (prestations listées), 3 (départements
couverts), 0 € (devis et déplacement annoncés gratuits).

---

## Médias

### Révision « pass finition » (17 juillet, après design-review)

Le hero est redevenu **la photo réelle du client** (tuile canal neuve + clocher + collines,
`hero-toiture.jpg` 1800px préchargée en LCP, `object-position: center 36%` desktop / `30% center`
mobile). Raison : le plan serré de stock ne disait ni « Ardèche » ni « résultat fini ». La vidéo
n'est pas perdue : elle vit dans la **carte bento « Rénovation de toiture »**, attachée et lue
uniquement quand la carte entre à l'écran (desktop, hors reduced-motion), avec fondu à la lecture
(`.playing`). Mobile : zéro octet de vidéo, vérifié.

**Révision du hero (choix Melvin, même jour)** : le hero est finalement
`roofer-installs-new-roof-tiles-on-sunny-day` (stock, geste de pose en lumière dorée, sujet à
droite) — 196 Ko desktop / 84 Ko mobile, `center 40%` desktop / `75% center` mobile. L'alt ne
prétend PAS que c'est un chantier du client. La carte bento 01 passe sur
`construction-workers-install-red-roofing` pour éviter le doublon hero/carte. La photo réelle
tuile canal + clocher reste disponible dans `assets/originaux/`.

Finitions ajoutées : `text-wrap: balance` (titres) et `pretty` (corps), `tabular-nums` (stats),
`::selection` accent, focus clair sur fonds sombres, FAQ en accordéon natif (`details name`),
pastille flèche des cartes assombrie (invisible sur ciel clair), règles print pour le texte blanc
des fonds sombres (les fonds ne s'impriment pas), preload hero 2 tailles.

### Vidéo (dans la carte bento)

Source : `~/Downloads/3386_Close_up_look_of_the_roofer_getting_off_the_nails.mov` — **79 Mo,
1920×1080, 7 s, codec Photo-JPEG**. Injouable sur le web en l'état.

Ni `ffmpeg` ni `brew` sur la machine : conversion via **`avconvert`** (le même outil que pour le
hero de Cycy). Résultats mesurés :

| Preset | Résolution | Poids |
|--------|-----------|-------|
| Preset1920x1080 | 1920×1080 | 9,0 Mo |
| Preset1280x720 | 1280×720 | 6,0 Mo |
| **Preset960x540** | **960×540** | **3,7 Mo** ← retenu |
| Preset640x480 | 640×480 | 2,0 Mo (cadrage 4:3 inutilisable) |
| PresetMediumQuality | 568×320 | 728 Ko (trop petit pour un hero) |

`--multiPass` ne change rien. Pour référence, le hero de Bretonnet fait **828 Ko en 2048×1080** —
`avconvert` n'expose aucun réglage de débit et ne peut pas s'en approcher. **Tâche T7 : recompresser
en H.264 CRF ou WebM dès que ffmpeg est disponible, cible ~800 Ko.**

**La vidéo est un bonus, jamais une dépendance.** Le `<video>` est servi en `preload="none"` et
**sans `<source>` dans le HTML** ; son `poster` est une vraie photo. Le JS n'attache la source
qu'au-dessus de 860px et hors `reduced-motion`. Conséquence : sans JS, sur mobile, ou en
mouvement réduit, le visiteur voit la photo et **ne télécharge pas les 3,7 Mo**.

### Photos

| Fichier | Source | Emploi |
|---------|--------|--------|
| `img/hero-mob.jpg` | stock — roofer-working-hard-on-a-sunny-day | poster vidéo + hero mobile |
| `img/s-renovation.jpg` | stock — roofer-installs-new-roof-tiles | bento 01 (carte feat) |
| `img/s-reparation.jpg` | stock — roofer-working-hard | bento 02 |
| `img/s-charpente.jpg` | stock — aerial-view-brick-house-wooden-roof-frame | bento 03 |
| `img/s-zinguerie.jpg` | stock — roofer-installing-shiny-red-metal-roof | bento 04 |
| `img/s-etancheite.jpg` | stock — stripped-wooden-roof-terrace | bento 05 |
| `img/s-combles.jpg` | stock — closeup-attic-window | bento 06 |
| `img/savoir-faire.jpg` | **client, réel** — couvreur sur toit, village + clocher | section sombre « Nos chantiers » |
| `img/charpente.jpg` | **client, réel** — pin blond sur pierre sèche | section intro |
| `img/demoussage-avant/apres.jpg` | **client, réel** | bloc démoussage |

**Séparation nette et assumée** : le stock **illustre le métier** dans les cartes bento ; les photos
**réelles du client prouvent le travail** et sont les seules légendées « chantier réel ».

Les URLs WordPress servaient des versions redimensionnées en 1024×768 — insuffisant pour du retina.
Les originaux (jusqu'à 2016×1512) ont été récupérés en retirant le suffixe de taille de l'URL.

**Pourquoi le comparateur avant/après a été abandonné (D4).** Les couples ne se comparent pas : le
couple chantier 1 est le même toit sous le même angle, mais l'« après » est gris et terne — un
visiteur non initié y lit une dégradation. Le couple chantier 2 oppose un intérieur à un extérieur.
Un curseur *force* la comparaison ; nourri au mauvais contenu, il argumente contre l'artisan. Le
couple chantier 1 est utilisé côte-à-côte dans le bloc démoussage, légendé honnêtement — et sert
d'accroche à l'hydrofuge coloré. Le défaut de la photo devient l'argument du service suivant.

---

## Révision « adaptation secteur » (17 juillet, sur retour Melvin : « trop IA, couleurs pas adaptées »)

La **structure** Bretonnet reste (bento, hero plein cadre, chips, stats, Bricolage + Inter) ;
tout ce qui disait « SaaS » ou « nettoyage » a été refait pour dire « couvreur » :

- **Palette** : le bleu `#1577cc` → **terre cuite** `#b4552d` (tuile), accent-deep `#8a3d1e`
  pour le texte (6,81:1), accent-bright `#e59a6b` sur fonds sombres (7,11:1). Fonds bleu-glacier
  → **papier pierre** `#f6f2ec`. Sections sombres bleu nuit → **charbon chaud** `#251f19`
  (ardoise brûlée/zinc). Neutres 100 % chauds, tous les rgba durs balayés (voiles, ombres,
  callbar, menu mobile). 6 contrastes mesurés, tous ≥ 4,91:1.
- **Vagues SVG → lignes de toit** (deux pans + faîtage, `M0,104 L820,24 L1440,88`) : les vagues
  sont sur la liste noire IA et n'avaient de sens que pour le nettoyage (eau).
- **Rayons resserrés** (8/10/14/18/24 au lieu de 10/14/20/28/40) — le tout-arrondi est un tell.
- **Pictogramme de marque** : maison générique → **toit à deux pans + cheminée**, décliné dans
  le favicon. `theme-color` → `#251f19`.
- **Grammaire éditoriale** (retour Melvin « classique/cheap », ex. section intro) : les
  pilules-icônes de tête de section → **kickers à filet** (trait terre cuite + capitales
  espacées) ; la liste à coches de l'intro → lead resserré (2 lignes) + **spécimen matériaux**
  en petites capitales ; les tuiles-icônes (section sombre, contact) et cartes blanches du
  process → **filets hairline** + numéros 01–04 ; les 17 pilules de communes et la bande
  « Également » → **texte à interponctions** terre cuite. Zéro coche, zéro pilule décorative,
  zéro carte non-interactive.
- **Hero dégraissé** (retour Melvin « trop de texte ») : budget affiche strict — chip zone (3 mots),
  H1, **une** phrase d'appui (« Couvreur artisan en Ardèche du Sud. Devis et déplacement
  gratuits. »), 2 CTA. Supprimés : l'énumération de 24 mots des prestations (elles titrent le
  bento), la décennale de la chip (portée par « Nos chantiers »), le bandeau de stats 11/3/0 €
  (info déjà dans bento, chip et process). CSS mort purgé.

## Design system — structure reprise de Bretonnet, habillage métier

### Palette (variables CSS, aucun hex en dur hors `:root`)

```
--ink        #0c2236   --bg     #eaf1f8   --surface #ffffff
--text       rgba(14,34,54,.86)           --text-mute #51677d
--accent     #1577cc   --accent-deep #0f5b9f   --accent-bright #3aa3e8
--navy-1     #0a1d33   --navy-2 #0e2a47
--r-xs 10px · --r-sm 14px · --r-md 20px · --r-lg 28px · --r-xl 40px
```

**Correctif d'accessibilité sur le système hérité** : `--accent` sur `--bg` ne donne que **4,06:1**,
sous le minimum AA de 4,5 pour du texte. Le texte de lien passe donc en `--accent-deep` (**6,11:1**) ;
`--accent` est réservé aux aplats (boutons, icônes, marque).

### Typographie

**Bricolage Grotesque** (600/700/800) en display · **Inter** (400/500/600/700) en corps.
Google Fonts avec `preconnect` — auto-hébergement en tâche T8.

### Motion

Entrée décalée du hero (`heroIn`, d1/d2/d3) · reveal on scroll via IntersectionObserver ·
hover des cartes bento (image `scale(1.06)` + élévation + flèche qui s'accentue).
`prefers-reduced-motion` coupe tout, y compris la vidéo.

---

## Structure de page

```
NAVBAR transparente → opaque au scroll (marque, liens, tél, Devis)
HERO vidéo plein cadre + 3 dégradés · chip · H1 Bricolage + <em> accent · sous-titre
     · 2 CTA · stats 11 / 3 / 0 € · VAGUE SVG
INTRO split — texte + photo RÉELLE (charpente pin blond sur pierre sèche)
SERVICES bento 6 cartes photo (feat 3×2 + 5) + bande « Également » 5 prestations = 11
SECTION SOMBRE « Nos chantiers » — vagues haut/bas, 4 arguments, photo RÉELLE
DÉMOUSSAGE — couple avant/après RÉEL côte à côte + encart hydrofuge coloré
PROCESS 4 étapes · ZONES 17 communes · FAQ 8 questions
CONTACT — formulaire + tél + SIRET · FOOTER · callbar mobile
+ schema.org RoofingContractor + FAQPage
```

---

## Vérification (preview réelle)

Serveur `http://localhost:4196`, viewports 1440×960 et 375×812. **0 erreur console.**

**Vérifié :** hero vidéo (lecture, dégradés, navbar lisible), bento 6 cartes (photos chargées,
titres lisibles), section sombre + vagues, bloc démoussage, formulaire, footer, navbar mobile,
menu burger, bascule vidéo→photo.

**Contrastes mesurés :** titres 14,21:1 · liens 6,11:1 (après correctif) · accent clair sur navy
6,13:1 · chip 6,05:1. **11 prestations couvertes** (6 cartes + 5 en bande). **0 champ sans label.**

### Bugs trouvés et corrigés en preview

| # | Bug | Cause | Correctif |
|---|-----|-------|-----------|
| 1 | Photo du hero tournée à 90° *(1ʳᵉ direction)* | `sips` inverse les dimensions sur ces photos de téléphone | `sips --rotate 270` + contrôle navigateur |
| 2 | Menu mobile visible sur desktop | `display:none` enfermé dans la media query | règle de base |
| 3 | Photos avant/après en 256×800 au lieu de 256×341 | l'attribut HTML `height` neutralise `aspect-ratio` | `img { height: auto }` |
| 4 | Cible tactile du burger à 20×44 | comprimé par le flex | `flex: none` |
| 5 | Liens du menu mobile inertes | `pointer-events:none` hérité de `.nav` | `pointer-events: auto` |
| 6 | Corps de texte à 14,7 px | `rem` se cale sur la racine, pas sur `body` | valeurs revues |
| 7 | **Texte blanc de la navbar invisible** | la vidéo a un **ciel cramé en blanc pur** au centre | 3ᵉ dégradé haut sur `.hero-media::after` |
| 8 | **Titres illisibles sur les cartes bento claires** | voile de Bretonnet calibré pour des photos sombres | voile renforcé (.96 → .42 à 62 %) |
| 9 | **Liens à 4,06:1 — échec AA** | `--accent` de Bretonnet trop clair sur `--bg` | texte en `--accent-deep` (6,11:1) |
| 10 | **Mobile téléchargeait les 3,7 Mo de vidéo** | la bascule dépendait d'un listener `matchMedia` | `<source>` attachée par JS au-dessus de 860px uniquement |
| 11 | Marque + chip cassées sur 2 lignes en mobile | descripteur trop long | masqué sous 860px |
| 12 | Titre du hero illisible sur mobile | photo ensoleillée, voile desktop trop faible au milieu | voile mobile dédié |

**Robustesse :** la révélation au défilement est en amélioration progressive (`<html class="js">`).
Sans JS, sans IntersectionObserver ou si les transitions ne tournent pas, tout le contenu reste
visible. La vidéo suit la même logique : sans JS, poster seul, zéro octet.

---

## NOT in scope (différé, avec raison)

- **Pages services individuelles** — le contenu scrapé ne suffit pas à nourrir 11 pages sans délayer.
- **Pages par commune** — 17 communes × page = usine à pages minces. À traiter en programmatique.
- **Refonte du logo en identité complète** (papeterie, véhicule, panneaux).
- **Blog** — aucun contenu source, personne pour l'alimenter.
- **Retouche colorimétrique des photos** — on ne « répare » pas un toit gris en post-production.

## Implementation Tasks

- [ ] **T1 (P1)** — formulaire — Renseigner la clé Web3Forms réelle (`index.html`). Bloque la mise en ligne.
- [ ] **T2 (P1)** — contact — Obtenir l'e-mail auprès du client. Absent du site source. Bloque la mise en ligne.
- [ ] **T5 (P2)** — conformité — Vérifier le label RGE : le site promet MaPrimeRénov' pour les combles, qui **exige** RGE.
- [ ] **T4 (P2)** — SEO — Ajouter `openingHours` au schema.org (horaires absents du site source).
- [ ] **T7 (P2)** — perf — **Recompresser la vidéo** : 3,7 Mo via `avconvert`, cible ~800 Ko (ffmpeg CRF ou WebM). Ni ffmpeg ni brew sur la machine.
- [ ] **T3 (P3)** — identité — Logo SVG définitif (le bloc bleu actuel est une marque typographique).
- [ ] **T6 (P3)** — photo — Demander zinguerie, combles, façade, hydrofuge coloré réels pour remplacer le stock.
- [ ] **T8 (P3)** — perf — Auto-héberger Bricolage Grotesque et Inter.

## GSTACK REVIEW REPORT

| Review | Trigger | Why | Runs | Status | Findings |
|--------|---------|-----|------|--------|----------|
| CEO Review | `/plan-ceo-review` | Scope & strategy | 0 | — | — |
| Codex Review | `/codex review` | Independent 2nd opinion | 0 | — | — |
| Eng Review | `/plan-eng-review` | Architecture & tests (required) | 0 | — | — |
| Design Review | `/plan-design-review` | UI/UX gaps | 2 | issues_open | score 2/10 → 9/10, 7 décisions, 12 bugs corrigés, direction refaite (D7) |
| DX Review | `/plan-devex-review` | Developer experience gaps | 0 | — | — |

- **VERDICT:** DESIGN CLEARED — direction Bretonnet construite et vérifiée en preview desktop et
  mobile. Site statique sans backend : eng review non requise. Les points ouverts sont des
  **données client**, pas des décisions design. T1 et T2 bloquent la mise en ligne.

**UNRESOLVED DECISIONS:**
- E-mail de contact — absent du site source ; le formulaire n'a pas de destinataire (bloque la mise en ligne)
- Clé Web3Forms — placeholder ; le formulaire bascule sur le repli téléphone (bloque la mise en ligne)
- Labels RGE / Qualibat — non sourcés, or MaPrimeRénov' pour l'isolation des combles exige RGE
- Horaires d'ouverture — absents du site source, donc absents de `openingHours`
- Poids de la vidéo — 3,7 Mo au lieu des ~800 Ko de Bretonnet ; bloqué par l'absence de ffmpeg sur la machine
- Compteurs chiffrés et réseaux sociaux — non repris tant que le client n'a pas fourni de vrais nombres et de vraies URLs
