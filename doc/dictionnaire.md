# Dictionnaire des variables

## Variables de la fiche d'opération standardisée

Ces variables sont systématiquement implémentées sur la base de la nature de l'opération.

| Code catégorie | Catégorie | Code | Description | Format | Exemple |
|:--------------:|:---------:|:----:|-------------|--------|:-------:|
| FOS | Fiche | $FOS.code | Code de la fiche | XXX-XX-XXX | BAR-TH-106 |
| FOS | Fiche | $FOS.secteur | Secteur d'application de la fiche | AGRI, BAR, BAT, IND, RES, TRA | BAR-TH-106 |
| FOS | Fiche | $FOS.volume_cee | Volume de CEE | float | Donnée calculée |

## Bâtiment résidentiel

### Données d'entrée

Ces variables sont construites sur la base des données d'entrée transmises.

| Code catégorie | Catégorie | Code | Description | Format | Exemple |
|:--------------:|:---------:|:----:|-------------|--------|:-------:|
| B | Bâtiment | $B.age | Ancienneté du bâtiment | integer | 10 |
| B | Bâtiment | $B.anciennete | Ancienneté du bâtiment | NEUF, EXISTANT | EXISTANT |
| B | Bâtiment | $B.energie_chauffage | Energie de chauffage principale du bâtiment | ELECTRICITE, GAZ_NATUREL, FIOUL, PAC, BOIS, GPL, CHARBON | ELECTRICITE |
| B | Bâtiment | $B.logements | Nombre de logements | float | 7 |
| B | Bâtiment | $B.surface_habitable | Surface habitable | float | 100 |
| B | Bâtiment | $B.type | Type de bâtiment | MAISON, APPARTEMENT, IMMEUBLE | MAISON |
| B | Bâtiment | $B.type_installation_chauffage | Type d'installation de chauffage | INDIVIDUEL, COLLECTIF | INDIVIDUEL |
| O | Opération | $O.besoin_annuel_ecs | Besoin annuel en eau chaude sanitaire à produire par l’énergie solaire exprimé (kW) | float | 12000 |
| O | Opération | $O.cef_initial | Consommation conventionnelle initiale (kWh/m²/an) | float | 450 |
| O | Opération | $O.cef_projet | Consommation conventionnelle après travaux (kWh/m²/an) | float | 150 |
| O | Opération | $O.code_departement | Code département du projet | XX | 84 |
| O | Opération | $O.consommation_suivie | Nature des consommations suivies par l'équipement installée | CHAUFFAGE_ELECTRIQUE, CHAUFFAGE_GAZ, ELECTRICITE_SPECIFIQUE | CHAUFFAGE_GAZ |
| O | Opération | $O.cop | Coefficient de performance énergétique | float | 3.8 |
| O | Opération | $O.diametre_nominal | Diamètre nominal de la canalisation (mm) | float | 80 |
| O | Opération | $O.duree_garantie_cpe | Durée de garantie du contrat de performance énergétique | integer | 5 |
| O | Opération | $O.etas | Efficacité énergétique saisonnière (ηs) de l'équipement (%) | float | 106.2 |
| O | Opération | $O.puissance_totale_bar_th_107 | Puissance totale des équipements relevant de la fiche BAR-TH-107 nouvellement installés (kW) | float | 200 |
| O | Opération | $O.puissance_totale_bar_th_150 | Puissance totale des équipements relevant de la fiche BAR-TH-150 nouvellement installés (kW) | float | 200 |
| O | Opération | $O.puissance_totale_bar_th_166 | Puissance totale des équipements relevant de la fiche BAR-TH-166 nouvellement installés (kW) | float | 200 |
| O | Opération | $O.puissance_totale_chaufferie | Puissance totale de la chaufferie après travaux (kW) | float | 200 |
| O | Opération | $O.indice_ik | Indice de résistance aux chocs | integer | 10 |
| O | Opération | $O.luminaire_detecteur_lumiere | Présence d'un détecteur de lumière | boolean | true |
| O | Opération | $O.luminaire_detecteur_presence | Présence d'un détecteur de présence | boolean | true |
| O | Opération | $O.option_suivi_confort | Présence d'une option "Suivi de confort" | boolean | true |
| O | Opération | $O.production_solaire_utile | Production solaire utile (kWh/an) | float | 3500 |
| O | Opération | $O.puissance_frigorifique | Puissance frigorifique de l'équipement (kW) | float | 1.8 |
| O | Opération | $O.puissance_nominale | Puissance nominale de l'équipement (kW) | float | 17 |
| O | Opération | $O.quantite_chaleur_nette | Chaleur nette unile produite par l'équipement (kWh/an) | float | 25000 |
| O | Opération | $O.quantite | Quantité de travaux | float | 100 |
| O | Opération | $O.resistance_isolant | Résistance thermique de l'isolant (m2.K/W) | float | 5.5 |
| O | Opération | $O.scop | Coefficient de performance saisonnier (SCOP) | float | 4.9 |
| O | Opération | $O.seer | Coefficient d'éfficacité énergétique saisonnier | float | 7 |
| O | Opération | $O.superficie_capteurs_solaires | Superficie des capteurs solaires installés (m²) | float | 6 |
| O | Opération | $O.temperature_fluide | Température du fluide caloporteur (°C) | float | 90 |
| O | Opération | $O.taux_couverture_ecs | Taux de couverture des besoins annuels d'ECS par l'équipement installée (%) | float | 67.5 |
| O | Opération | $O.taux_couverture_solaire | Taux de couverture solaire de l'installation | float | 0.8 |
| O | Opération | $O.type_caisson_vmc | Type de caisson de VMC simple flux | BASSE_CONSOMMATION, STANDARD, BASSE_PRESSION | STANDARD |
| O | Opération | $O.type_cesc | Type de chauffe-eau solaire collectif | CESC, CESCI | CESCI |
| O | Opération | $O.type_chauffe_bain | Type de chauffe bain | HAUT_RENDEMENT, CONDENSATION | HAUT_RENDEMENT |
| O | Opération | $O.type_extracteur | Type d'extracteur de ventilation | STANDARD, BASSE_CONSOMMATION | STANDARD |
| O | Opération | $O.type_installation | Type d'installation | INDIVIDUEL, COLLECTIF | INDIVIDUEL |
| O | Opération | $O.type_point_singulier | Type de poins singulier | HORS_ECHANGEUR, ECHANGEUR | ECHANGEUR |
| O | Opération | $O.type_usage | Type d'usage de l'équipement installé | CHAUFFAGE_ECS, ECS | CHAUFFAGE_ECS |
| O | Opération | $O.type_vmc_hygroreglable | Type de ventilation hygroréglable | TYPE_A, TYPE_B | TYPE_A |
| O | Opération | $O.type_vmc_double_flux | Type de VMC double flux | AUTOREGLABLE, MODULE | MODULE |

### Données intermédiaires

Ces variables sont calculées sur la base des données d'entrée transmises.

| Code catégorie | Catégorie | Code | Description | Format | Exemple |
|:--------------:|:---------:|:----:|-------------|--------|:-------:|
| B | Bâtiment | $B.energie_chauffage_alt | Energie de chauffage principale du bâtiment | ELECTRICITE, COMBUSTIBLE | Donnée calculée |
| O | Opération | $O.facteur_correctif_rch | Facteur correctif de la part des équipements éligibles dans la nouvelle chaufferie | float | Donnée calculée |
| O | Opération | $O.facteur_correctif_sch_5 | Facteur correctif selon la surface chauffée | float | Donnée calculée |
| O | Opération | $O.facteur_correctif_sch_7 | Facteur correctif selon la surface chauffée | float | Donnée calculée |
| B | Bâtiment | $B.facteur_correctif_shab_4 | Facteur correctif selon la surface habitable | float | Donnée calculée |
| B | Bâtiment | $B.facteur_correctif_shab_5 | Facteur correctif selon la surface habitable | float | Donnée calculée |
| B | Bâtiment | $B.facteur_correctif_shab_7 | Facteur correctif selon la surface habitable | float | Donnée calculée |
| O | Opération | $O.taux_couverture_solaire_plafond | Taux plafond de couverture par l’énergie solaire de l’installation (80%) | float | Donnée calculée |
| O | Opération | $O.zone_climatique | Zone climatique du projet | H1, H2, H3 | Donnée calculée |
