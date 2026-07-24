# Debord Rénovation — mise en place trafic (SEO, GEO, Ads)

Site en ligne sur `https://renovation-ardeche.fr` (Cloudflare + dépôt
`netfox-agency/debordrenovation`). Ce qui est **fait dans le code** et ce qui
**reste à faire côté comptes** (impossible depuis le code : email, Google, etc.).

---

## FAIT (code, déjà poussé)

- **12 pages prestation** en URL propre, contenu métier unique, schema
  `Service` + `BreadcrumbList` + `FAQPage`, canonical, maillage interne.
- **URLs propres partout** (canonical, og, sitemap, llms, liens) : plus de
  redirection 307 `.html` → `/page` sur les landing pages (bon pour le SEO et
  pour le Quality Score des ads).
- **GEO** : `llms.txt` + `robots.txt` autorisant GPTBot, ClaudeBot,
  PerplexityBot, OAI-SearchBot, Google-Extended…
- **Suivi de conversions prêt** : `dataLayer` pousse `generate_lead` (devis
  envoyé) et `phone_call` (clic sur le numéro). GTM en attente d'un vrai ID.
- **Page 404** aux couleurs du site, `_headers` (cache 1 an sur assets,
  en-têtes sécurité), `_redirects` (www → apex), sitemap 13 URLs.

---

## À FAIRE — par ordre d'impact

### 1. Formulaire = destinataire — FAIT (clé Web3Forms câblée le 24/07)
Sans ça, chaque clic d'annonce qui remplit le formulaire tombe sur le repli
« appelez-nous » : lead à moitié perdu, budget ads gaspillé.

- **Il faut l'e-mail du client** (probablement `…@renovation-ardeche.fr`, la
  boîte OVH). Deux options, 2 minutes :
  - **Web3Forms** (déjà câblé) : créer une clé gratuite sur web3forms.com avec
    cet e-mail, puis remplacer `REMPLACER_PAR_CLE_WEB3FORMS` dans `index.html`.
  - **FormSubmit** (zéro inscription) : remplacer l'action du `<form>` par
    `https://formsubmit.co/<email>` (activation par un 1er e-mail de confirmation).
- Tester : remplir le formulaire, vérifier la réception.

### 2. Google Business Profile (le plus gros levier local)
Pour « couvreur ardèche », « couvreur aubenas », le pack local Google pèse plus
que le site. À créer / revendiquer sur business.google.com avec **exactement**
ce NAP (doit être identique au site, au caractère près) :

- **Nom** : Debord Rénovation
- **Catégorie principale** : Couvreur — **Secondaires** : Charpentier,
  Entreprise d'isolation, Entreprise de rénovation
- **Adresse** : 8 Impasse Louis Lauriol, 07170 Lavilledieu (zone de chalandise :
  tout le 07 + limitrophes 30/26 ; si intervention à domicile, masquer l'adresse
  et déclarer la zone)
- **Téléphone** : 06 66 14 37 84
- **Site** : https://renovation-ardeche.fr
- **Services** : reprendre les 12 (rénovation toiture, réparation/fuite,
  charpente, zinguerie, faîtage, étanchéité toit plat, isolation combles,
  démoussage, hydrofuge, façade, entretien, **sarking**).
- **Description** : « Couvreur artisan en Ardèche du Sud. Rénovation de toiture
  (tuile canal, ardoise, lauze), charpente, zinguerie, étanchéité, isolation des
  combles et sarking, démoussage, hydrofuge, façade. Devis et déplacement
  gratuits, garantie décennale. »
- **Photos** : les vraies photos de chantier (charpente, démoussage, toitures
  du village) — les mêmes que sur le site.
- **Avis** : demander un avis à chaque client satisfait (levier n°1 du pack local).

### 3. Google Search Console
- Vérifier le domaine (l'enregistrement TXT `google-site-verification` existe
  déjà dans le DNS — la propriété est peut-être déjà validée).
- **Soumettre le sitemap** : `https://renovation-ardeche.fr/sitemap.xml`.
- Demander l'indexation des 12 pages prestation (Inspection d'URL → Demander
  l'indexation), en priorité l'accueil, rénovation-toiture et sarking.

### 4. Suivi de conversions (pour les ads)
Les événements sont déjà émis, il reste à les brancher :
1. Créer un conteneur **Google Tag Manager**, remplacer `GTM-XXXXXXX` dans
   `assets/script.js` par son ID (puis bump `?v=9` → `?v=10`).
2. Dans GTM : déclencheurs sur les événements `generate_lead` et `phone_call`.
3. Créer une propriété **GA4** + les **actions de conversion Google Ads**
   (Devis = `generate_lead`, Appel = `phone_call`), reliées via GTM.
4. Résultat : chaque devis et chaque appel remonte comme conversion dans Ads.

### 5. Google Ads — structure recommandée
- **1 page = 1 groupe d'annonces** : le site est déjà fait pour ça (une landing
  par prestation, en URL propre, message aligné sur la requête → bon Quality Score).
- Campagnes prioritaires (intention haute) : « réparation fuite toiture »,
  « rénovation toiture », « sarking » (peu concurrentiel, CPC bas), « isolation
  combles » (aides = fort volume).
- Extensions : lieu (via GBP), appel (le 06), liens annexes vers les pages
  prestation.
- Ciblage géo : Ardèche + rayon sur Aubenas / Privas / Annonay / Le Teil.

### 6. Domaine www
Ajouter `www.renovation-ardeche.fr` comme domaine custom du Worker dans
Cloudflare : le fichier `_redirects` le redirigera alors vers l'apex.

---

## Après chaque déploiement
Cloudflare redéploie depuis GitHub à chaque push. Si le live ne reflète pas la
dernière version : onglet **Deployments** du Worker (vérifier que le build a
tourné), sinon **Purge cache** (Caching → Purge Everything).
