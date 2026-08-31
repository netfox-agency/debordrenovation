# Prompt : exploiter Search Console pour maximiser trafic et demandes

Copie tout ce qui suit dans une nouvelle session Claude Code, ouverte dans le
dossier `debord-renovation-refonte`.

---

Utilise le skill **claude-seo** pour ce travail.

## Contexte

Site : **https://renovation-ardeche.fr** (Debord Rénovation, couvreur artisan,
Lavilledieu 07170). Statique, hébergé sur Cloudflare Pages, `push main` =
redéploiement automatique. Repo `netfox-agency/debordrenovation`.

Objectif business : **des appels et des demandes de devis**, pas du trafic
décoratif. Le client tourne aussi en Google Ads sur 6 pages d'atterrissage,
budget 400 €/mois. Rayon d'intervention 100 km max autour de Lavilledieu.

Structure : 35 pages indexables.
- 1 accueil, 1 page réalisations
- 12 pages prestations, dont 6 servent de pages d'atterrissage publicitaires
  (`reparation-fuite-toiture-ardeche`, `demoussage-toiture-ardeche`,
  `hydrofuge-toiture-ardeche`, `zinguerie-ardeche`,
  `renovation-toiture-ardeche`, `etancheite-toit-plat-ardeche`)
- 18 pages de ville `couvreur-<ville>`
- 3 guides (`prix-renovation-toiture-ardeche`,
  `demoussage-ou-hydrofuge-toiture`, `fuite-toiture-que-faire`)

## Ce qui est DÉJÀ fait, ne le refais pas

Vérifie-le rapidement, mais ne repars pas de zéro :
- Sitemap propre, 35 URLs, `lastmod` réels issus de git, sans `changefreq` ni
  `priority`. Envoyé et lu par Search Console, 35 pages découvertes.
- Titles : 35/35 entre 30 et 60 caractères, aucun doublon.
- Meta descriptions : 35/35 entre 120 et 158 caractères, aucun doublon.
- H1 unique par page, hiérarchie de titres sans saut.
- Pages de ville : 80 % de contenu unique, 483 mots de moyenne.
- Schema JSON-LD : RoofingContractor, Service, WebPage, BreadcrumbList,
  FAQPage, Article, avec `datePublished` et `dateModified` sur les 35.
- Maillage interne : 809 liens, 0 cassé, 0 page orpheline, minimum 7 liens
  entrants par page de ville.
- Vitesse : FCP 112-140 ms, TTFB 37-74 ms, HTML 6-13 Ko, hero préchargé,
  images différées.
- robots.txt autorise GPTBot, OAI-SearchBot, ClaudeBot, PerplexityBot,
  Google-Extended. `llms.txt` présent et complet.

## Ce que je te fournis

J'exporte depuis Search Console et je te donne les fichiers :

1. **Performances → Résultats de recherche**, 3 derniers mois, export complet
   (onglets Requêtes, Pages, Pays, Appareils). Bouton Exporter en haut à droite.
2. **Indexation → Pages** : export du rapport, avec le détail des pages non
   indexées et leur motif.
3. **Expérience → Core Web Vitals** : capture ou export si des URLs sont
   signalées.
4. **Liens** : export des liens externes et internes.

Si un export manque, demande-le-moi avant de conclure quoi que ce soit.
Ne devine jamais des chiffres Search Console.

## Ce que je veux que tu analyses

### 1. Ce qui rapporte déjà
- Requêtes avec des impressions mais un CTR faible (moins de 2 % en position
  1 à 10) : le title ou la description ne donne pas envie. Propose des
  réécritures, chiffres à l'appui.
- Requêtes en position 11 à 20 : ce sont les gains les plus rapides. Identifie
  quelle page les capte et ce qui lui manque pour passer en page 1.
- Requêtes où une mauvaise page se positionne (cannibalisation) : deux pages
  qui visent la même intention se pénalisent.

### 2. Ce qui ne se voit pas
- Requêtes commerciales sur lesquelles le site n'apparaît pas du tout alors
  qu'une page existe.
- Requêtes de ville, service par service, en croisant avec les 18 pages de
  ville : lesquelles ne rankent sur rien ?
- Écarts entre les 6 pages d'atterrissage publicitaires : celles qui ne
  rankent pas en organique coûtent doublement, puisque tout le trafic y est payé.

### 3. Indexation
- Pour chaque motif de non-indexation, dis-moi la cause réelle et si c'est
  normal ou à corriger. Distingue « Découverte, non indexée » (attente) de
  « Explorée, actuellement non indexée » (signal de qualité insuffisante).
- Si des pages de ville sont concernées, croise avec leur taux de contenu
  unique et leur nombre de liens entrants.

### 4. Intention commerciale
Classe les requêtes par intention : urgence (fuite, tempête), entretien
(démoussage, hydrofuge), gros chantier (rénovation, charpente), information
(prix, comparatifs). Dis-moi où va le trafic aujourd'hui et où sont les
demandes de devis. L'urgence et le gros chantier valent bien plus que
l'information.

## Ce que je veux que tu produises

1. **Un diagnostic chiffré**, pas des généralités. Chaque constat s'appuie sur
   une donnée Search Console que tu cites.
2. **Une liste d'actions classées par impact estimé sur les demandes de devis**,
   pas par facilité. Pour chacune : la page concernée, ce qui change, le gain
   attendu et sur quelle donnée tu te bases.
3. **Applique directement** ce qui relève du code invisible (titles,
   descriptions, schema, maillage interne, sitemap). Commits atomiques, un par
   type de correction, message explicite.
4. **Propose sans exécuter** tout ce qui modifie l'affichage (nouvelles
   sections, tableaux, réécriture de contenu visible, changement de structure
   de page). J'ai le dernier mot dessus.
5. **Vérifie en production** après chaque déploiement, avec des mesures, pas
   des suppositions.

## Contraintes fermes

- **N'invente jamais de fait.** Pas de chantier fictif, pas d'avis inventé, pas
  de statistique non sourcée. Si tu as besoin d'un fait local, vérifie-le.
- **Aucune mention de Claude ou d'IA** dans quoi que ce soit de visible par le
  client ou ses visiteurs.
- **Pas de tirets cadratins** dans la copie du site : deux-points, virgules ou
  interpoints.
- **Ne touche pas à l'UI ni à l'UX** sans mon accord explicite : le SEO ne
  modifie que du code invisible.
- **Ne pousse pas sur `main` sans me le dire** : ça redéploie le site en ligne.
- Si tu trouves un défaut dans mon travail précédent, dis-le franchement avec
  la mesure qui le prouve.

## Rappel de priorité

Trois choses pèsent plus lourd que le site pour un artisan local, et elles ne
sont pas réglées. Si tu les vois dans les données, remonte-les :
1. La fiche Google Business Profile (facteur numéro un du pack local)
2. Les avis Google : il n'y en a que 3
3. Les citations locales et la cohérence nom/adresse/téléphone
