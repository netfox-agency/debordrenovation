# Analyse de rentabilité Google Ads — Debord Rénovation

Modèle d'économie unitaire pour maximiser le ROI. **Chiffres à recalculer avec
les VRAIS chiffres après 4 semaines** (valeur réelle des chantiers, taux de
transformation réel, CPC réels). En attendant : hypothèses explicites + fourchettes.

## Hypothèses (milieu de fourchette)

| Levier | Hypothèse | Fourchette |
|---|---|---|
| Marge artisan | 30 % | 25-40 % (repair/démoussage plus haut, rénovation plus bas) |
| Taux conv. landing (clic→lead) | 10 % | 8-14 % |
| Taux transfo (lead→chantier) | variable/presta | 20-50 % |
| CPC | par campagne | voir tableau |

## Économie unitaire par prestation

`Valeur d'un lead (en marge) = profit du chantier × taux de transfo`
`CPL réel = CPC ÷ taux de conversion` · `ROAS = valeur du lead ÷ CPL`

| Prestation | Chantier moyen | Profit/chantier | Transfo lead→chantier | **Valeur/lead** | CPC | CPL réel | **ROAS (sur marge)** |
|---|---|---|---|---|---|---|---|
| **Rénovation** | ~10 000 € | ~2 500 € | 20 % | **500 €** | 3,0 € | ~30 € | **≈ 16 x** |
| **Étanchéité** | ~2 200 € | ~660 € | 30 % | **198 €** | 2,5 € | ~25 € | **≈ 8 x** |
| **Démoussage** | ~1 200 € | ~480 € | 35 % | **168 €** | 1,8 € | ~18 € | **≈ 9 x** |
| **Gouttière** | ~700 € | ~245 € | 40 % | **98 €** | 1,8 € | ~18 € | **≈ 5,4 x** |
| **Fuite/urgence** | ~450 € | ~160 € | 45 % | **71 €** | 3,5 € | ~35 € | **≈ 2 x** |
| **Marque** | mix | ~450 € | 50 % | 225 € | 0,4 € | ~3 € | ≈ 80 x |

## Seuils CPL / CPA à NE JAMAIS dépasser (point mort)

Le **break-even = valeur du lead**. Au-delà, tu perds de l'argent sur le lead.
En Google Ads, le « CPA cible » se règle sur le **coût par LEAD** (appel/devis).

| Prestation | CPL max absolu (break-even) | **CPA cible conseillé** (marge saine) |
|---|---|---|
| Rénovation | 500 € | **≤ 60 €** |
| Étanchéité | 198 € | **≤ 35 €** |
| Démoussage | 168 € | **≤ 30 €** |
| Gouttière | 98 € | **≤ 30 €** |
| Fuite/urgence | 71 € | **≤ 35 €** |

> Le CPL **atteignable** (18-35 €) est très en-dessous du break-even partout →
> grosse marge de sécurité. Le vrai risque n'est PAS le CPC, c'est la **qualité
> des leads** (leads qui ne se transforment pas).

## Le point mort qui compte vraiment : le taux de transformation

À quel taux de transfo (lead→chantier) chaque campagne devient rentable :

| Prestation | Transfo MINIMUM pour être rentable |
|---|---|
| Rénovation | **1,2 %** (ultra-tolérant : 1 chantier paie ~80 leads) |
| Démoussage | 4 % |
| Étanchéité | 4 % |
| Gouttière | 7 % |
| **Fuite/urgence** | **22 %** (le plus tendu : petit chantier + CPC cher) |

→ **Fuite est la seule campagne « fragile »** : il lui faut > 22 % de transfo.
Si les leads fuite closent bien (urgence = forte intention), OK. Sinon, plafonne
son CPC dur. Rénovation/démoussage sont quasi impossibles à rendre déficitaires.

## Classement rentabilité (ROI réel)

1. **Rénovation** — meilleur ROAS (1 chantier = énorme), MAIS volume faible, cycle long, plus de concurrence, leads moins sûrs.
2. **Démoussage** — excellent ROAS **+ volume + cycle court** → **meilleur risque/rendement**.
3. **Étanchéité** — excellent ROAS, bon ticket.
4. **Gouttière** — très bon, clics pas chers.
5. **Fuite/urgence** — ROAS le plus faible MAIS **cash rapide + remplit l'agenda + priorité client**. À garder, CPC plafonné.
6. **Marque** — efficacité max, protège, tout petit volume.

**Cœur d'efficacité (le plus sûr) = Démoussage + Étanchéité + Gouttière.**
**Pari haut rendement = Rénovation.** **Cash rapide = Fuite.**

## Projection pour ~950 €/mois (allocation optimisée)

| Campagne | Budget/mois | CPL | Leads | Transfo | Chantiers | CA estimé |
|---|---|---|---|---|---|---|
| Démoussage | 210 € | 18 € | ~11,7 | 35 % | ~4,1 | ~4 900 € |
| Rénovation | 210 € | 30 € | ~7,0 | 20 % | ~1,4 | ~14 000 € |
| Fuite/urgence | 210 € | 35 € | ~6,0 | 45 % | ~2,7 | ~1 200 € |
| Étanchéité | 140 € | 25 € | ~5,6 | 30 % | ~1,7 | ~3 700 € |
| Gouttière | 120 € | 18 € | ~6,7 | 40 % | ~2,7 | ~1 900 € |
| Marque | 60 € | ~3 € | (limité) | 50 % | ~3,0 | ~4 500 € |
| **Total** | **~950 €** | | **~40 leads** | | **~15-16 chantiers** | **~30 000 €** |

- **Scénario réaliste** : ~30 000 € de CA → ~9 000 € de marge pour **950 €** de pub → **ROI ≈ +850 %** (ROAS marge ≈ 9-10 x).
- **Scénario conservateur** (CVR 8 %, CPC +30 %, transfo −25 %, rénovation 0-1 chantier) : ~12-15 000 € CA, ~4-5 000 € marge → **ROI ≈ +350-450 %**.
- ⚠️ **Rénovation pèse ~40 % du CA sur 1-1,4 chantier** = forte variance. La **base sûre** (démoussage+fuite+gouttière+étanchéité) = ~9-11 chantiers, ~11-15 000 € CA, régulier.

## Allocation budget optimale (max ROI)

- Démoussage **22 %**, Rénovation **22 %**, Fuite **22 %**, Étanchéité **15 %**, Gouttière **13 %**, Marque **6 %**.
- Après 4 semaines de data : **couper les campagnes < seuil**, remettre le budget sur les **CPA les plus bas qui transforment** (règle 70/20/10).

## Leviers concrets pour protéger la marge

1. **Suivi conversions + call tracking OBLIGATOIRE** (sinon pilotage à l'aveugle). Le vrai risque = leads pourris invisibles.
2. **CPA cible** (une fois ~15 conv) réglé sous le break-even (tableau ci-dessus). Surtout sur **Fuite** (marge tendue).
3. **CPC max plafonné** dès le départ (Fuite 4 €, Rénovation 3 €, autres 2-2,5 €).
4. **Géo serré par campagne** (Fuite/gouttière 40 km, démoussage/étanchéité 60 km, rénovation 100 km) : ne pas payer des leads trop loin qui ne closent pas.
5. **Négatifs agressifs** (emploi, formation, 1€, gratuit, DIY, matériaux…) + **exact/phrase** au début, **jamais large**.
6. **Termes de recherche vérifiés chaque semaine** → négatifs.
7. **Boucle qualité lead** : noter quels leads deviennent chantiers → plus tard, **importer les conversions hors ligne** dans Google Ads pour qu'il optimise vers les **chantiers signés**, pas juste les leads. C'est LE levier avancé de rentabilité.
8. **Message aligné landing/annonce** (déjà fait) = Quality Score haut = CPC plus bas.
9. **Fuite 24h/24** (intention max le week-end), autres heures ouvrées.

## À recalculer avec les vrais chiffres (mois 2)
Remplacer : valeur moyenne réelle par prestation, taux de transfo réel (leads→devis→chantiers signés), CPC réels observés. Le modèle se resserre et on réalloue sur les gagnantes.
