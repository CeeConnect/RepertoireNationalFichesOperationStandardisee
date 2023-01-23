# @ceeconnect - Répertoire national des fiches d'opération standardisée

Version 0.9

⚠️ Développement en cours.

## Couverture

### Fiches d'opération standardisée

- AGRI
- BAR
- BAT
- IND
- RES
- TRA

### Bonifications

- AGRI
- BAR
- BAT
- IND
- RES
- TRA

## Dictionnaire des balises

### Fiches

| Balise | Description | Requis | Format | Exemple |
|:------:|-------------|:------:|--------|:-------:|
| id | Identifiant unique de la fiche | Oui | Concaténation du code et de la version | BAR-TH-101v17-4 |
| version | Version de l'enregistrement | Oui | Arrêté cible au format XX.XX | 14.1 |
| secteur | Secteur d'application | Oui | AGRI, BAR, BAT, IND, RES, TRA | AGRI |
| sous_secteur | Sous-secteur d'application | Oui | Bâtiments, Chaleur et Froid, Eclairage, Enveloppe, Equipement, Services, Thermique, Utilités | EQ |
| code | Code de l'entité | Oui | XXX-XX-XXX | BAR-EN-101 |
| date_debut | Date d'entrée en vigueur de la fiche | Oui | yyyy-mm-dd | 2022-01-01 |
| date_find | Date d'abrogation de la fiche | Non | yyyy-mm-dd | 2023-01-01 |
| nom | Nom de l'entité | Oui | Chaîne de caractères | Isolation des combles |
| url | URL d'accès à la fiche au format PDF | Oui | URL | http://calculateur-cee.ademe.fr/pdf/display/286/BAR-EN-101 |
| metropole | Application de la fiche en france métropolitaine | Oui | Boolean | 1 |
| outre_mer | Application de la fiche en france d'outre-mer | Oui | Boolean | 1 |
| conditions | Liste des conditions d'application de la fiche | Oui | Element composé | cf [Condition](#condition) |
| regles | Liste des règles de calcul de la fiche | Oui | Element composé | cf [Regle](#regle) |

* La version des fiches d'opération standardisée est égale à la version de l'arrêté applicable


⚠️ Une fiche est applicable dès sa date d'entrée en vigueur, et ne l'est plus à sa date d'abrogation.

#### Bâtiment résidentiel

| Balise | Description | Requis | Format | Exemple |
|:------:|-------------|:------:|--------|:-------:|
| maison | Application de la fiche aux maisons individuelles | Oui | Boolean | 1 |
| appartement | Application de la fiche aux appartements | Oui | Boolean | 1 |
| immeuble | Application de la fiche aux immeubles collectifs | Oui | Boolean | 1 |

### Bonifications

### Condition

| Balise | Description | Requis | Format | Exemple |
|:------:|-------------|:------:|--------|:-------:|
| description | Description de la condition | Oui | Chaine de caractères - CDATA | Bâtiment existant |
| expression | Expression à résoudre | Oui | Expression | cf [Expression](#expression) |

### Regle

| Balise | Description | Requis | Format | Exemple |
|:------:|-------------|:------:|--------|:-------:|
| description | Description de la règle | Oui | Chaine de caractères - CDATA | Zone climatique - H1 |
| conditions | Conditions | Non | Conditions | cf [Condition](#condition) |
| expression | Expression à résoudre | Oui | Expression | cf [Expression](#expression) |

### Expression

Une expression peut être :

- Une valeur numérique
- Une référence à une variable
- Une opération arithmétique
- Une comparaison

##### Cas des valeurs numérique

La valeur numérique est stockée sous forme de chaine de caractères.

````
<expression><![CDATA[1200]]></expression>
````

##### Cas des références à une variable

La référence est stockée sous forme de chaine de caractères.

````
<expression><![CDATA[$O.volume_cee_fiche]]></expression>
````

##### Cas d'opération arithmétique

L'opération arithmétique est stockée sous forme de chaine de caractères en utilisant le formatage requis des variables.

````
<expression><![CDATA[1400 * $O.quantite]]></expression>
````

##### Cas d'une comparaison

La comparaison est stockée sous forme de chaine de caractères en utilisant le formatage requis des variables.

````
<expression><![CDATA[$O.zone_climatique === 'H2']]></expression>
<expression><![CDATA[$O.etas >= 102 && $O.etas < 110]]></expression>
````

###### Opérateurs de comparaison

| Exemple | Nom | Résultat |
|:-------:|:---:|:--------:|
| $a == $b | Egal | $a est identique à $b après transtypage |
| $a === $b | Identique | $a est identique à $b et sont du même type |
| $a != $b | Différent | $a est différent de $b après transtypage |
| $a !== $b | Différent | $a est différent de $b ou ne sont pas du même type |
| $a > $b | Supérieur | $a est supérieur à $b |
| $a >= $b | Supérieur ou égal | $a est supérieur ou égal à $b |
| $a < $b | Inférieur | $a est inférieur à $b |
| $a <= $b | Inférieur ou égal | $a est inférieur ou égal à $b |

### Bonifications


## Dictionnaire des variables

### Variables communes

| Code catégorie | Catégorie | Code | Description | Format | Exemple |
|:--------------:|:---------:|:----:|-------------|--------|:-------:|
| FOS | Fiche | $FOS.code | Code de la fiche | XXX-XX-XXX | BAR-TH-106 |
| FOS | Fiche | $FOS.secteur | Secteur d'application de la fiche | AGRI, BAR, BAT, IND, RES, TRA | BAR-TH-106 |
| FOS | Fiche | $FOS.volume_cee | Volume de CEE | float | Donnée calculée |

### Bâtiment résidentiel

#### Données d'entrée

| Code catégorie | Catégorie | Code | Description | Format | Exemple |
|:--------------:|:---------:|:----:|-------------|--------|:-------:|
| B | Bâtiment | $B.age | Ancienneté du bâtiment | integer | 10 |
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
| O | Opération | $O.q_chaleur_nette | Chaleur nette unile produite par l'équipement (kWh/an) | float | 25000 |
| O | Opération | $O.quantite | Quantité de travaux | float | 100 |
| O | Opération | $O.resistance_isolant | Résistance thermique de l'isolant (m2.K/W) | float | 5.5 |
| O | Opération | $O.scop | Coefficient de performance saisonnier (SCOP) | float | 4.9 |
| O | Opération | $O.seer | Coefficient d'éfficacité énergétique saisonnier | float | 7 |
| O | Opération | $O.superficie_capteurs_solaires | Superficie des capteurs solaires installés (m²) | float | 6 |
| O | Opération | $O.t_fluide | Température du fluide caloporteur (°C) | float | 90 |
| O | Opération | $O.taux_couverture_ecs | Taux de couverture des besoins annuels d'ECS par l'équipement installée (%) | float | 67.5 |
| O | Opération | $O.taux_couverture_solaire | Taux de couverture solaire de l'installation | float | 0.8 |
| O | Opération | $O.type_caisson_vmc_simple_flux | Type de caisson de VMC simple flux | BASSE_CONSOMMATION, STANDARD, BASSE_PRESSION | STANDARD |
| O | Opération | $O.type_cesc | Type de chauffe-eau solaire collectif | CESC, CESCI | CESCI |
| O | Opération | $O.type_chauffe_bain | Type de chauffe bain | HAUT_RENDEMENT, CONDENSATION | HAUT_RENDEMENT |
| O | Opération | $O.type_extracteur | Type d'extracteur de ventilation | STANDARD, BASSE_CONSOMMATION | STANDARD |
| O | Opération | $O.type_installation | Type d'installation | INDIVIDUEL, COLLECTIF | INDIVIDUEL |
| O | Opération | $O.type_point_singulier | Type de poins singulier | HORS_ECHANGEUR, ECHANGEUR | ECHANGEUR |
| O | Opération | $O.type_usage | Type d'usage de l'équipement installé | CHAUFFAGE_ECS, ECS | CHAUFFAGE_ECS |
| O | Opération | $O.type_ventilation_hygroreglable | Type de ventilation hygroréglable | TYPE_A, TYPE_B | TYPE_A |
| O | Opération | $O.type_vmc_double_flux | Type de VMC double flux | AUTOREGLABLE, MODULE | MODULE |
| O | Opération | $O.type_vmc_simple_flux | Type de VMC simple flux | TYPE_A, TYPE_B | TYPE_A |

#### Données intermédiaires

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

## Releases


## 🤔 Foire aux questions

### Les fiche BAR-TH-110, BAR-TH-116, BAR-TH-117 et BAR-TH-158 sont-elles éligibles aux immeubles collectifs ?

Recherche en cours...

### Quelles sont les différences entre $O.facteur_correctif_shab_x et $O.facteur_correctif_schb_x ?

Les facteurs correctifs selon la surface habitable ou chauffée se déclinent en plusieurs tableaux selon les fiches d'opération standardisée :

| Facteur correctif - Maison | Facteur correctif - Appartement | Surface habitable / Surface chauffée S en m² |
|:----------------:|:-------------------------:|
| 0.3 | 0.5 | S < 35 |
| 0.5 | 0.7 | 35 ≤ S < 60 |
| 0.6 | 1 | 60 ≤ S < 70 |
| 0.7 | 1.2 | 70 ≤ S < 90 |
| 1 | 1.5 | 90 ≤ S < 110 |
| 1.1 | 1.9 | 110 ≤ S <= 130 |
| 1.6 | 2.5 | S > 130 |

7 lignes correspondant à la variable **$O.facteur_correctif_shab_7** et **$O.facteur_correctif_sch_7**.

| Facteur correctif - Maison | Surface habitable / Surface chauffée S en m² |
|:----------------:|:-------------------------:|
| 0.5 | S < 70 |
| 0.7 | 70 ≤ S < 90 |
| 1 | 90 ≤ S < 110 |
| 1.1 | 110 ≤ S <= 130 |
| 1.6 | S > 130 |

5 lignes correspondant à la variable **$O.facteur_correctif_shab_5** et **$O.facteur_correctif_sch_5**.

| Facteur correctif - Maison | Surface habitable S en m² |
|:----------------:|:-------------------------:|
| 0.7 | S < 70 |
| 0.9 | 70 ≤ S < 90 |
| 1 | 90 ≤ S <= 130 |
| 1.2 | S > 130 |

4 lignes correspondant à la variable **$O.facteur_correctif_shab_4**.

Recherche en cours...

## Todo

- **BAR-TH-159** : Mettre à jour la nouvelle fiche en vigueur au 01/04/2023 dès parution
- **BAR-TH-160** : Mettre à jour la nouvelle fiche en vigueur au 01/04/2023 dès parution
