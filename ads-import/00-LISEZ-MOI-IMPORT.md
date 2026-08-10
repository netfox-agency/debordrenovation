# Import des campagnes dans Google Ads

**Contenu :** 4 campagnes · 9 groupes d'annonces · 107 mots-clés · 9 annonces RSA
· 1 liste de négatifs. Plan 400 €/mois.

> ⚠️ **Les campagnes arrivent en PAUSE, volontairement.** Rien ne se dépense tant
> que tu ne les actives pas. On les active seulement après avoir branché le suivi
> de conversions et l'extension d'appel (sinon on paie à l'aveugle).

---

# ▶ MÉTHODE A — Actions groupées (interface web) ← celle que tu veux

**Un seul fichier : `IMPORT-GOOGLE-ADS.csv`** (129 lignes : les campagnes, les
groupes, les mots-clés et les annonces, dans l'ordre).

1. Dans le compte **Debord Rénovation** (pas le MCC), menu de gauche :
   **Actions groupées → Importations** (ou « Chargements »).
2. Bouton **+** → **Importer un fichier** → sélectionner `IMPORT-GOOGLE-ADS.csv`.
3. Google affiche un **aperçu**. Vérifier : 4 campagnes, 9 groupes, 107 mots-clés,
   9 annonces. **Regarder la colonne des erreurs.**
4. Cliquer **Appliquer**.

> 💡 Si l'aperçu montre des erreurs (ça arrive : l'import web est plus capricieux
> que Google Ads Editor pour créer des campagnes de zéro), passe à la **méthode B**,
> qui est plus fiable. Les deux produisent exactement le même résultat.

---

# MÉTHODE B — Google Ads Editor (plus fiable, si A coince)

## Étape 1 — Installer Google Ads Editor
Télécharger sur `ads.google.com/home/tools/ads-editor/` (Mac/Windows, gratuit).
Se connecter avec `netfox.france@gmail.com` → télécharger le compte
**Debord Rénovation** (il apparaît sous le MCC Netfox).

## Étape 2 — Importer les fichiers, DANS CET ORDRE
Menu **Compte → Importer → À partir d'un fichier**, un fichier à la fois :

| Ordre | Fichier | Ce que ça crée |
|---|---|---|
| 1 | `01-campagnes.csv` | Les 4 campagnes (en pause) |
| 2 | `02-groupes-annonces.csv` | Les 9 groupes d'annonces |
| 3 | `03-mots-cles.csv` | Les 107 mots-clés (exact + expression) |
| 4 | `04-annonces-rsa.csv` | Les 9 annonces responsives |

À chaque import, Editor affiche un **aperçu des changements** : vérifier qu'il n'y
a pas d'erreur en rouge, puis valider. Puis **Publier** en haut à droite.

## Étape 3 — Réglages à faire à la main (non importables)
Ces réglages passent mal en CSV, on les fait dans Editor ou dans l'interface web.
**Ils sont indispensables**, surtout le ciblage géographique.

### Ciblage géographique (LE plus important)
Pour chaque campagne : **rayon autour de Lavilledieu 07170**
- `Search_Urgence-Reparation_Ardeche` → **40 km**
- `Search_Entretien-Toiture_Ardeche` → **60 km**
- `Search_Gros-Chantiers_Ardeche` → **100 km**
- `Search_Marque_Ardeche` → **100 km**

Et dans les options de zone, choisir **« Personnes présentes dans vos zones ciblées »**
(surtout PAS « présence ou intérêt » : sinon on paie des clics de gens qui ne sont
pas dans la zone).

### Réseaux
Décocher **Réseau Display** et **partenaires du réseau de recherche** sur les 4 campagnes.

### Négatifs
Créer une **liste de mots-clés à exclure partagée** (Outils → Listes de mots-clés
à exclure), coller le contenu de `05-mots-cles-negatifs.txt`, puis l'appliquer aux
4 campagnes.

### Extensions (au niveau du compte)
- **Extension d'appel** : 06 66 14 37 84 → c'est elle qui compte les appels comme conversions.
- **Extension de lieu** : relier la fiche Google Business.
- **Liens annexes** : Réparation & fuite, Démoussage, Rénovation, Réalisations.
- **Accroches** : Devis gratuit · Déplacement gratuit · Garantie décennale · Artisan local · Intervention rapide.

### Calendrier de diffusion
Diffuser **quand Debord peut décrocher**. Un appel manqué = 100 % du clic perdu :
c'est le premier poste de gaspillage à ce budget.

## Étape 4 — Publier
Bouton **« Publier »** en haut à droite d'Editor. Les campagnes montent dans le
compte, **en pause**.

## Étape 5 — Avant d'activer (ne pas sauter)
1. **Facturation** : carte / IBAN de Debord en place.
2. **Suivi de conversions** : GTM branché (`generate_lead` + `phone_call`, déjà
   codés sur le site) et testé.
3. **Extension d'appel** active.
4. Alors seulement : passer les campagnes en **Activées**.

---

## Rappel des budgets
| Campagne | €/jour | €/mois |
|---|---|---|
| Urgence & réparation | 4,61 | 140 |
| Entretien toiture | 4,28 | 130 |
| Gros chantiers | 3,29 | 100 |
| Marque | 0,99 | 30 |
| **Total** | **13,17** | **400** |

## Si l'import bloque
- **Erreur d'encodage / accents bizarres** : les fichiers sont en UTF-8 avec BOM,
  ce qu'Editor attend. Ne pas les rouvrir/réenregistrer dans Excel (il casse l'encodage).
- **« Campagne introuvable »** : c'est que l'ordre n'a pas été respecté (les
  campagnes doivent exister avant les groupes, etc.).
- **Annonce refusée** : vérifier qu'aucun titre ne dépasse 30 caractères. Ils ont
  tous été validés automatiquement, donc ça ne devrait pas arriver.
