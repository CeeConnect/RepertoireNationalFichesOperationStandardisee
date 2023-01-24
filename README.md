# @ceeconnect - Répertoire national des fiches d'opération standardisée

Version 0.9

⚠️ Développement en cours.

## Spécifications

### Identification des entités

#### Fiches d'opération standardisée

Chaque fiche est identifiée par un ID unique composé du **code** mentionné par la fiche concernée et par la **version** applicable de l'arrêté (cf [versionnement](###Versionnement)).

Exemple:

| Fiche | Arrêté | Version | ID |
|:-----:|:------:|:-------:|:--:|
| BAR-TH-159 | A44-3 | 44.3 | BAR-TH-159v44-3 |
| BAR-TH-159 | A50-4 | 50.4 | BAR-TH-159v50-4 |

#### Bonifications

Chaque bonification est identifiée par un ID unique composé du **code** selon [l'annexe 6](https://www.legifrance.gouv.fr/loda/article_lc/LEGIARTI000044200266) de l'arrêté du 4 septembre 2014 fixant la liste des éléments d'une demande de certificats d'économies d'énergie et les documents à archiver par le demandeur, le cas échéant du **code da la fiche d'opération standardisée applicable**, et de la **version** applicable (cf [versionnement](###Versionnement)).
 
Exemple:

| Bonification | Fiche | Version | ID |
|:------------:|:-----:|:-------:|:--:|
| CDP | BAR-TH-104 | 10 | CDP-BAR-TH-104v10 |
| CDP | BAR-TH-104 | 11 | CDP-BAR-TH-104v11 |
| ZNI | - | 1 | ZNIv1 |

### Versionnement

### Fiches d'opération standardisée

Le versionnement appliqué reprend la version de l'[arrêté](https://www.legifrance.gouv.fr/loda/id/JORFTEXT000029953752/) du 22 décembre 2014 définissant les opérations standardisées d'économies d'énergie applicable.

### Bonifications

Le versionnement sur la base réglementaire n'est que partiellement applicable compte tenu de la structure législative des bonifications, lesquelles sont définies (et regroupées) par plusieurs articles de l'[arrêté](https://www.legifrance.gouv.fr/loda/id/JORFTEXT000030001603) du 29 décembre 2014 relatif aux modalités d'application du dispositif des certificats d'économies d'énergie.

Il est donc retenu le versionnement suivant :

- Le versionnement comment au 01/01/2022
- La première version de chaque entité reprend la version applicable de l'article applicable au sein de l'arrêté du 29 décembre 2014 à cette date
- La modification de l'article applicable au sein de l'arrêté du 29 décembre 2014 **entrainant une modification des conditions d'application et/ou de calcul des montants de la bonification** a pour conséquence la création d'une nouvelle entité dont la version sera prise égale à la nouvelle version de l'article modificatif.

### Applications

- Une entité est applicable dès sa date d'entrée en vigueur, et ne l'est plus à sa date d'abrogation.
- Une entité est toujours applicable à au moins l'une des deux zones géographiques suivantes : France métropolitaine et/ou France d'outre mer

## Règles de gestion

### Expression

Une expression peut être :

- Une valeur numérique
- Une référence à une variable
- Une opération arithmétique
- Une comparaison

#### Cas des valeurs numérique

La valeur numérique est stockée sous forme de chaine de caractères.

````
<expression><![CDATA[1200]]></expression>
````

#### Cas des références à une variable

La référence est stockée sous forme de chaine de caractères.

````
<expression><![CDATA[$O.volume_cee_fiche]]></expression>
````

#### Cas d'opération arithmétique

L'opération arithmétique est stockée sous forme de chaine de caractères en utilisant le formatage requis des variables.

````
<expression><![CDATA[1400 * $O.quantite]]></expression>
````

#### Cas d'une comparaison

La comparaison est stockée sous forme de chaine de caractères en utilisant le formatage requis des variables.

````
<expression><![CDATA[$O.zone_climatique === 'H2']]></expression>
<expression><![CDATA[$O.etas >= 102 && $O.etas < 110]]></expression>
````

Liste des opérateurs de comparaison :

| Exemple | Nom | Résultat |
|:-------:|:---:|:--------:|
| $\$a == \$b$ | Egal | $\$a$ est identique à $\$b$ après transtypage |
| $\$a === \$b$ | Identique | $\$a$ est identique à $\$b$ et sont du même type |
| $\$a != \$b$ | Différent | $\$a$ est différent de $\$b$ après transtypage |
| $\$a !== \$b$ | Différent | $\$a$ est différent de $\$b$ ou ne sont pas du même type |
| $\$a > \$b$ | Supérieur | $\$a$ est supérieur à $\$b$ |
| $\$a >= \$b$ | Supérieur ou égal | $\$a$ est supérieur ou égal à $\$b$ |
| $\$a < \$b$ | Inférieur | $\$a$ est inférieur à $\$b$ |
| $\$a <= \$b$ | Inférieur ou égal | $\$a$ est inférieur ou égal à $\$b$ |

## 🤔 Foire aux questions

### Quelles sont les différences entre \$O.facteur_correctif_shab_x et \$O.facteur_correctif_schb_x ?

Les facteurs correctifs selon la surface habitable ou chauffée se déclinent en plusieurs tableaux selon les fiches d'opération standardisée :

| Facteur correctif - Maison | Facteur correctif - Appartement | Surface habitable / Surface chauffée S en m² |
|:----:|:----:|:----:|
| 0.3 | 0.5 | S < 35 |
| 0.5 | 0.7 | 35 ≤ S < 60 |
| 0.6 | 1 | 60 ≤ S < 70 |
| 0.7 | 1.2 | 70 ≤ S < 90 |
| 1 | 1.5 | 90 ≤ S < 110 |
| 1.1 | 1.9 | 110 ≤ S <= 130 |
| 1.6 | 2.5 | S > 130 |

7 lignes correspondant à la variable **\$O.facteur_correctif_shab_7** et **\$O.facteur_correctif_sch_7**.

| Facteur correctif - Maison | Surface habitable / Surface chauffée S en m² |
|:----:|:----:|
| 0.5 | S < 70 |
| 0.7 | 70 ≤ S < 90 |
| 1 | 90 ≤ S < 110 |
| 1.1 | 110 ≤ S <= 130 |
| 1.6 | S > 130 |

5 lignes correspondant à la variable **\$O.facteur_correctif_shab_5** et **\$O.facteur_correctif_sch_5**.

| Facteur correctif - Maison | Surface habitable S en m² |
|:----:|:----:|
| 0.7 | S < 70 |
| 0.9 | 70 ≤ S < 90 |
| 1 | 90 ≤ S <= 130 |
| 1.2 | S > 130 |

4 lignes correspondant à la variable **\$O.facteur_correctif_shab_4**.

