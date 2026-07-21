# Debord Rénovation — site vitrine

Site statique one-page (HTML/CSS/JS pur, aucun build) pour Debord Rénovation
(marque commerciale de Rénovation Ardèche), couvreur en Ardèche du Sud.

## Lancer en local

    python3 -m http.server 8788

## Structure

    index.html              page unique
    mentions-legales.html   mentions légales + RGPD
    assets/styles.css       design system complet (variables CSS)
    assets/script.js        nav, reveal, FAQ, formulaire
    assets/img/             photos optimisées (chantiers réels du client)
    assets/originaux/       sources pleine résolution (non versionnées)

## Avant mise en ligne — bloquants

1. **Clé Web3Forms** — remplacer `REMPLACER_PAR_CLE_WEB3FORMS` dans `index.html`.
   Tant qu'elle est absente, le formulaire bascule sur le repli téléphone (par
   conception : on n'envoie jamais dans le vide).
2. **E-mail de contact** — absent du site source. À obtenir du client.

## À demander au client

- Labels RGE / Qualibat (l'isolation des combles avec MaPrimeRénov' **exige** RGE).
- Horaires d'ouverture (pour `openingHours` dans le schema.org).
- Chiffres réels si les compteurs doivent revenir (ancienneté, chantiers réalisés).
- URLs réelles des réseaux sociaux — sur le site actuel, les 5 liens pointent sur `#`.
  Non affichés ici tant qu'ils n'existent pas.
- Photos de zinguerie, combles, façade, faîtage, hydrofuge coloré : aucune n'existe
  aujourd'hui, ce qui a dicté le parti pris de l'index typographique.

## Intégrité du contenu

Tout le contenu est repris du site existant ou de ses mentions légales. Aucun avis,
aucune note, aucun chiffre, aucun prix et aucun label n'a été inventé.
