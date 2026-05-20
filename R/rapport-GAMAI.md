---
title: "Rapport de groupe des UE \\newline  Bases de données + Sciences des Données 2"
author:
- 'Ejebli Adem, '
- Haki Moatacem,
- Ikdoumi Ilian,
- Zizi Ahmed.
date: "04 mai 2026"
output:
  pdf_document:
    fig_caption: yes
    keep_md: yes
    keep_tex: yes
    md_extensions: +raw_attribute
    number_sections: yes
    pandoc_args:
    - --top-level-division="chapter"
    - --bibliography="references.bib"
    template: template.tex
    toc: yes
    toc_depth: 1
  word_document:
    fig_caption: yes
    number_sections: yes
    pandoc_args: 
    - --top-level-division="chapter"
    - --to="odt+native_numbering"
    toc: yes
    toc_depth: '2'
  html_document:
    df_print: paged
    toc: yes
    toc_depth: '2'
toc-title: "Table des matières"
bibliography: references.bib
coursecode: TV15MI-TV25MI
csl: iso690-author-date-fr-no-abstract.csl
Acknowledgements: Nos plus sincères remerciements vont à Madame BRINGAY Sandra pour tous les enseignements qu'elle nous a apportés lors de ce semestre dans le cadre du cours de Bases de Données. Nous la remercions également pour tous les conseils précieux qu'elle nous a donnés semaine après semaine, ainsi que pour le temps qu'elle a pris pour répondre à nos questions, aussi bien en classe que par mail.Nous remercions également Madame DEMANGEOT Marine pour tous les cours de Sciences des Données 2 qu'elle nous a dispensés et pour nous avoir appris le langage R. Nous la remercions particulièrement pour ses conseils avisés sur la réalisation des différents graphiques et sur la démarche d'analyse statistique à suivre pour mener à bien ce projet.
biblio-style: elsarticle-harv
session: 2026
team: AMAI
groupeTD : TD1 
Abstract: Dans le cadre de notre deuxième année à l'Université Paul Valéry, nous présentons ce projet transversal qui lie nos deux enseignements de Bases de Données et de Sciences des Données 2. Notre équipe, nommée AMAI (pour Ahmed, Moatacem, Adem et Ilian), a choisi d'étudier l'influence du cadre de vie d'un pays sur son niveau de sécurité global. L'objectif de ce travail est de comprendre si des facteurs concrets comme l'urbanisation massive, la richesse économique ou encore le taux de chômage sont les causes directes de l'insécurité, ou si des disparités géographiques et culturelles persistent malgré le développement d'un pays. Pour répondre à cette problématique, nous avons croisé des données mondiales de 2023 portant sur les indices de criminalité de plus de 400 villes avec des indicateurs socio-économiques nationaux. Ce projet repose sur une double approche technique afin de traiter nos données de manière rigoureuse. Dans un premier temps, nous avons utilisé le langage SQL pour structurer notre base de données, importer nos fichiers et effectuer des requêtes complexes permettant d'extraire les informations pertinentes pour notre sujet. Ce travail sur les bases de données nous a permis de filtrer les variables inutiles et de préparer un jeu de données propre pour l'analyse. Dans un second temps, nous avons utilisé le logiciel R et l'interface RStudio pour réaliser une analyse exploratoire approfondie. Enfin, notre démarche vise à proposer une interprétation globale de nos résultats en mettant en perspective les données chiffrées avec la réalité du terrain. En comparant les différentes régions du monde, nous cherchons à identifier si la richesse est réellement le facteur numéro un de la tranquillité d'un pays ou si la gestion de l'urbanisation et les politiques sociales jouent un rôle plus important. Ce rapport détaille ainsi l'ensemble de notre processus, depuis la modélisation conceptuelle de nos données jusqu'aux conclusions statistiques, afin d'apporter des éléments de réponse précis sur les facteurs qui influencent réellement la sécurité à l'échelle mondiale. .\newline
  
always_allow_html: true
---




# Introduction {.label:s-intro}

## Contenu d'une introduction

Le sentiment de sécurité est l'un des piliers du bien-être des populations et du développement des pays. Pourtant, les niveaux de criminalité varient énormément d'une ville à l'autre à travers le monde, sans que l'on puisse toujours en expliquer les raisons exactes. C'est pourquoi notre étude se concentre sur les villes, en tant qu'unités d'analyse privilégiées pour observer ces disparités. Comme le montrent Nelly Exbrayat, Victor Stephane ( Does Urbanization Cause Crime? Evidence from Rural-Urban Migration in South Africa. 2024. ⟨halshs-04390026 ⟩ ( accessible ici : _https://shs.hal.science/halshs-04390026)  ), le processus d'urbanisation joue un rôle complexe sur la criminalité, en interaction avec des facteurs économiques et sociaux tels que le chômage ou les inégalités de revenus. Est-ce une question de richesse pure ? Est-ce la conséquence d'une urbanisation trop rapide ? Ou existe-t-il des facteurs culturels et géographiques qui l'emportent sur l'économie ?


\bigskip

\begin{center}

\textbf{Dans quelle mesure le mode de développement d'un pays (urbanisation, économie et géographie) influence-t-il le niveau de sécurité de ses villes ?}

\end{center}
\medskip 

\justifying

L'étude de la sécurité est aujourd'hui un enjeu majeur car elle impacte directement la qualité de vie des citoyens, la santé mentale des populations et la liberté de mouvement au quotidien. Pour les décideurs publics et les urbanistes, comprendre si l'urbanisation massive dégrade la sécurité est essentiel pour construire les villes de demain de manière plus humaine et mieux organisée. Enfin, sur le plan économique, un environnement sûr est indispensable pour rassurer les investisseurs et favoriser le développement durable des entreprises locales.

\medskip



\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip
\bigskip

## \textbf{Responsabilités et composition de l’équipe}

\bigskip
\bigskip
\bigskip

\textbf{Adem EJEBLI :} Étudiant n°22407392 Resp du MCD. Resp du tri des données. Coresp. du rapport. Coresp de l’importation des données. Coresp. des requêtes SQL. Coresp. de l’analyse des données.

\bigskip
\bigskip

\textbf{Moatacem HAKI :} Étudiant n°22408182. Coresp. du MCD. Coresp du tri des données. Resp du rapport. Resp de l’importation des données. Resp des requêtes SQL. Coresp. de l’analyse des données.


\bigskip
\bigskip

\textbf{Ilian IKDOUMI :} Étudiant n°22404947. Coresp du MCD. Coresp du tri des données. Resp du rapport. Coresp. de l’importation des données. Coresp. des requêtes SQL. Resp. de l’analyse des données.

\bigskip
\bigskip

\textbf{Ahmed ZIZI :} Étudiant n°22414136. Coresp. du MCD. Coresp. du tri des données. Coresp. du rapport. Resp. de l’importation des données. Coresp. des requêtes SQL. Resp de l’analyse des données.

\medskip




# Base de données

## Provenance des données

Pour mener à bien cette étude transversale, nous avons sélectionné deux jeux de données complémentaires sur la plateforme Kaggle afin de croiser les indicateurs de sécurité urbaine avec les données socio-économiques mondiales de l'année 2023. Le premier jeu de données, intitulé World Crime Index 2023 (disponible sur kaggle.com/datasets/arsalanrehman/world-crime-index-2023), recense les indices de criminalité et de sécurité pour 416 villes mondiales. Le second, Global Country Information Dataset 2023 ( kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023), regroupe des statistiques macro-économiques et démographiques par nation.



\bigskip


Nous avons choisi ces deux sources car elles contiennent les variables indispensables pour tester nos hypothèses sur l'urbanisation, la richesse et la géographie. Les données sont stockées au format CSV. Le fichier sur la criminalité comporte initialement 416 lignes et 5 colonnes, tandis que le fichier sur les informations mondiales contient 195 lignes et 35 colonnes. L'observation de ces données montre que nous disposons en moyenne d'environ 4 villes par pays, ce qui assure une base statistique cohérente pour nos analyses comparatives. Cette structure nous permet de travailler sur des échelles différentes, allant de la métropole précise au pays entier.


\bigskip

Afin de réduire le périmètre du projet et de garantir la pertinence de nos analyses, nous avons filtré les colonnes pour ne conserver qu'une dizaine de variables sur les 40 disponibles au total. Nous avons gardé les indicateurs liés à l'économie comme le PIB ou le chômage, à la démographie avec la population urbaine et la densité, ainsi qu'à la localisation spatiale. Un choix important de notre nettoyage a été de retirer systématiquement du jeu de données les pays pour lesquels nous n'avions aucune ville associée avec un indice de criminalité, afin d'assurer une fusion cohérente et exploitable entre nos deux tables.

\bigskip

La population étudiée correspond donc aux métropoles et aux nations disposant de données complètes pour l'année 2023. Les unités statistiques sont la ville, pour l'analyse précise des indices de criminalité, et le pays, pour caractériser le cadre de vie général. Le croisement de ces données nous permet d'apporter des éléments de réponse à notre problématique en observant comment le développement global d'un pays influence directement la sécurité de ses zones urbaines.


## Descriptif des tables



| Nom colonne  | Type   | Signification    | Caractéristique |
|--------------|--------|------------------|-----------------|
| city_id      | Entier | Identifiant      | Unique          |
| city_name    | Texte  | Nom de la ville  | Nom de la ville |
| crime_index  | Réel   | Indice de crime  | Indice de criminalité ( en pourcentage)  |
| country_name | Texte  | Nom du pays      | Clé étrangère   |

Table: City (416 $\times$ 4)


| Nom colonne                      | Type         | Signification         | Caractéristique                               |
|----------------------------------|--------------|-----------------------|-----------------------------------------------|
| country_name                     | Texte        | Nom du pays           | Clé primaire                                  |
| population_density               | Décimal      | Densité population    | Nombre d'habitants par km2                    |
| armed_forces_size                | Entier       | Taille armée          | Nombre de militaires actifs                   |
| birth_rate                       | Décimal      | Taux de natalité      | Nombre de naissances pour 1000 habitants      |
| cpi                              | Décimal      | Indice prix conso     | Mesure de l'inflation                         |
| gdp                              | Entier       | Richesse (PIB)        | Produit Intérieur Brut en dollars             |
| primary_ed_enrol_pct             | Décimal      | Scolarité primaire %  | Taux d'inscription au primaire                |
| tertiary_ed_enrol_pct            | Décimal      | Scolarité tertiaire % | Taux d'inscription au supérieur               |
| life_expectancy                  | Décimal      | Espérance de vie      | Âge moyen de décès                            |
| minimum_wage                     | Décimal      | Salaire minimum       | Revenu minimum légal                          |
| total_population                 | Entier       | Population totale     | Nombre total d'habitants                      |
| labor_particip_rate              | Décimal      | Taux activité         | Pourcentage de population active              |
| unemployment_rate                | Décimal      | Taux de chômage       | Pourcentage de chômeurs                       |
| urban_population                 | entier       | Population urbaine    | Nombre d'habitants en ville                   |
| latitude                         | Décimal      | Position Nord/Sud     | Coordonnée géographique Latitude              |
| longitude                        | Décimal      | Position Est/Ouest    | Coordonnée géographique Longitude             |


Table: Country (195 $\times$ 16)

## Modèles MCD et MOD



  ![MCD](MCD.jpeg){#uml width="8cm" height="4cm"}
  




\bigskip
  ![MOD](MOD.jpeg){#uml width="8cm" height="4cm"}




## Import des données 

Source de données 1 : crime-index-2023

Dans un premier temps, nous avons travaillé sur la base de données crime-index-2023. Nous avons remarqué que la colonne Country contenait des espaces inutiles, ce qui empêchait de comparer efficacement les noms de pays entre les deux bases de données. 
Nous avons donc créé une nouvelle colonne en appliquant la formule =SUPPRESPACE(A2) afin de supprimer ces espaces.

Ensuite, nous avons créé une colonne temporaire permettant de vérifier si chaque pays de crime-index-2023 était bien présent dans world-data-2023, grâce à la formule =NB.SI('world-data-2023'!A:A;D2). Cette formule retourne 1 si le pays existe dans l'autre base de données, et 0 dans le cas contraire. En analysant les résultats, nous avons constaté que les États américains et les provinces canadiennes étaient représentés séparément (NY, TX, FL, etc.). Nous les avons donc tous remplacés par United States et Canada via la fenêtre de remplacement (Ctrl+H). 
Nous avons également supprimé les enregistrements dont les pays n'étaient pas présents dans world-data-2023, à savoir l'Irlande, Porto Rico et Taïwan.
Nous avons vérifié l'absence de doublons dans cette base de données. Aucun doublon n'a été détecté, ce qui est cohérent étant donné que les unités statistiques sont des villes, qui sont par nature des entrées uniques.

																				
Source de données 2 : world-data-2023

Dans un second temps, nous avons travaillé sur la base de données world-data-2023. Celle-ci contenait initialement une trentaine de colonnes, représentant des indicateurs très variés tels que le prix de l'essence, et d' autres encore. Nous avons donc supprimé toutes les colonnes que nous n'utilisions pas dans le cadre de notre étude, afin de ne conserver que les variables pertinentes pour répondre à notre problématique, à savoir celles liées à l'économie, à la démographie et à la géographie des pays.
\bigskip
Nous avons ensuite ajouté une colonne permettant de compter le nombre de villes associées à chaque pays dans crime-index-2023, grâce à la formule =NB.SI($'crime-index-2023_clean (2)'.D:D;world_data_2023[[#Cette ligne];[Country]]). Cette formule parcourt la colonne D de crime-index-2023 et compte combien de fois le nom du pays apparaît. Un résultat de 0 signifie qu'aucune ville de ce pays n'est présente dans notre base de criminalité. Nous avons donc supprimé toutes les lignes correspondant à ces pays, car sans ville associée, ils ne pouvaient contribuer à aucune de nos analyses. Nous avons remarqué que la grande majorité de ces pays sans ville associée étaient des pays de petite taille disposant de peu de données à l'échelle internationale.

Par ailleurs, lors de ce tri, nous avons vérifié la présence de valeurs vides dans l'ensemble des colonnes. Certains pays comme la Corée du Nord présentaient de nombreuses valeurs manquantes pour la quasi-totalité des indicateurs, en raison du manque de données disponibles à leur sujet. Ces pays ont donc été supprimés directement, d'autant plus qu'ils ne disposaient généralement d'aucune ville associée dans notre base de criminalité.
\bigskip

Durant cette vérification des valeurs manquantes, nous avons également remarqué que la colonne minimum_wage contenait des valeurs nulles pour un certain nombre de pays, tels que l'Italie, la Suisse, la Norvège ou encore le Danemark. Après plusieurs recherches, nous avons constaté que ces pays ne disposent tout simplement pas de salaire minimum officiel fixé par l'État, les salaires étant déterminés par des conventions collectives sectorielles. Nous avons donc décidé de conserver ces valeurs nulles telles quelles, car elles reflètent une réalité juridique et non une erreur dans les données.
\bigskip

Enfin, nous avons remarqué que les colonnes gdp et minimum_wage contenaient des valeurs au format texte, précédées du symbole $ et, pour le PIB, avec des virgules comme séparateurs de milliers (par exemple $1,234,567,890). Ce format aurait posé problème lors de nos futures requêtes SQL, car ces valeurs n'auraient pas été reconnues comme des nombres. Nous avons donc supprimé le symbole $ ainsi que les virgules dans ces deux colonnes en utilisant la commande de remplacement Ctrl+H sur LibreOffice Calc, en remplaçant ces caractères par une valeur vide.
\medskip

De la même manière, nous avons constaté que les colonnes « Gross primary education enrollment (%) », « Gross tertiary education enrollment (%) » et « Population: Labor force participation (%) » contenaient le symbole %. Afin d’éviter tout problème de traitement des données, nous avons également supprimé ce symbole en utilisant la commande Ctrl+H, en le remplaçant par une valeur vide.
\medskip

Plus globalement, un nettoyage approfondi a été nécessaire pour garantir la 
compatibilité des données avec les requêtes SQL. Dans l'ensemble des 
colonnes numériques — telles que GDP, Population, ou encore les différents 
taux (chômage, éducation, participation au marché du travail) — nous avons 
supprimé toutes les virgules servant de séparateurs de milliers ainsi que les 
symboles parasites (%, $). Cette étape est indispensable car, lors de 
l'importation en base de données, la présence d'un caractère non numérique 
force SQL à interpréter la colonne comme du texte (VARCHAR), ce qui rend 
impossible tout calcul mathématique tel qu'une somme, une moyenne ou une 
comparaison numérique. Nous avons également veillé à ce que le seul 
séparateur décimal utilisé soit le point (.), conformément au standard SQL, 
permettant ainsi de définir correctement les types de données en BIGINT ou 
FLOAT selon les cas.
\medskip

Concernant la colonne minimum_wage, nous avions précédemment décidé de 
conserver les valeurs nulles correspondant aux pays sans salaire minimum 
légal. Cependant, afin de permettre une importation correcte de la base de 
données, nous avons remplacé ces cellules vides par la valeur NULL à l'aide de 
la commande Ctrl+H, en substituant les cellules vides par le mot-clé NULL. 
Cette manipulation est nécessaire car un champ vide et une valeur NULL ne 
sont pas équivalents en SQL : un champ vide peut être interprété comme une 
chaîne de caractères vide, ce qui provoquerait une erreur de type lors de 
l'importation dans une colonne numérique.
\medskip

Nous avons vérifié l'absence de doublons dans cette base de données. Aucun doublon n'a été détecté, ce qui est cohérent étant donné que les unités statistiques sont des pays, qui sont par nature des entrées uniques.

\bigskip
\bigskip
\bigskip

## Requêtes réalisées

Requête 1 : Le contraste Richesse (PIB) / Sécurité (HAVING + ORDER BY + Jointure classique)
\medskip

Langage naturel : Afficher le PIB des pays présentant soit une criminalité moyenne très élevée (indice > 70), soit très faible (indice < 30), classés du plus dangereux au plus sûr.
\medskip

    SQL :

    SELECT country.country_name, AVG(city.crime_index) AS crime_moyen, country.gdp
    FROM city, country
    WHERE city.country_name = country.country_name
    GROUP BY country.country_name, country.gdp
    HAVING AVG(city.crime_index) > 70 OR AVG(city.crime_index) < 30
    ORDER BY crime_moyen DESC;
    




![Requête_1](R1.png){#uml width="4cm" height="8cm"}

\medskip

Interpretation  :   

Cette requête est vraiment intéressante car elle permet de mettre en évidence un contraste assez fort entre le développement économique d'un pays et le niveau de sécurité de ses habitants. En isolant les deux extrêmes de notre base de données, on remarque tout de suite un point important : avoir un gros PIB ne protège pas forcément de la criminalité. On voit par exemple que des pays comme le Venezuela ou l'Afrique du Sud ont des richesses mondiales importantes, mais affichent pourtant des indices de crime au dessus de 80. Cela montre bien que d'autres facteurs, comme les inégalités sociales ou les tensions politiques, pèsent parfois plus lourd que la simple richesse brute. À l'inverse, pour les pays les plus sûrs comme le Qatar, les Émirats ou la Suisse, la corrélation semble plus logique : un PIB très élevé s'accompagne d'une criminalité très basse. Enfin, pour les nations qui cumulent un petit PIB et une forte insécurité, comme l'Afghanistan, on comprend que le manque de ressources économiques est un facteur aggravant. En résumé, si la richesse d'un pays aide souvent à maintenir l'ordre, elle n'est pas une solution magique et le contexte social reste la variable principale pour expliquer ces écarts.

\bigskip
\bigskip
\bigskip


Requête 2 : Impact du chômage sur les zones critiques (INNER JOIN)                                                                                                                                                
\medskip

Langage naturel : Lister les villes ayant un indice de criminalité critique (> 70) avec le taux de chômage du pays correspondant.
\medskip

    SQL :


    SELECT city.city_name, city.crime_index, country.unemployment_rate
    FROM city
    INNER JOIN country ON city.country_name = country.country_name
    WHERE city.crime_index > 70;
    




![Requête_2](R2.png){#uml width="4cm" height="7cm"}

\medskip

Interpretation  :   

Les résultats obtenus mettent en évidence un ensemble de villes dont l'indice de criminalité dépasse le seuil critique de 70, réparties dans plusieurs pays aux profils économiques très différents. On remarque que les villes d'Afrique du Sud — Pretoria, Durban, Johannesburg et Cape Town — sont toutes associées au taux de chômage le plus élevé de l'échantillon, soit 28,18 %, ce qui suggère un lien possible entre un chômage structurellement élevé et une forte criminalité. À l'inverse, des villes comme Port Moresby (2,46 %) ou Lima (3,31 %) affichent des taux de chômage faibles malgré un indice de criminalité très élevé, ce qui indique que le chômage seul n'est pas un facteur suffisant pour expliquer la criminalité. Les villes américaines présentes dans ce classement — Baltimore, Memphis, Detroit, Albuquerque — partagent le même taux de chômage national de 14,70 %, ce qui place les États-Unis parmi les pays développés les plus représentés dans cette liste. De manière générale, ces résultats suggèrent que la criminalité est un phénomène multifactoriel qui ne peut pas être réduit au seul taux de chômage, et qu'il convient de croiser cette donnée avec d'autres indicateurs économiques et sociaux pour en avoir une lecture plus complète.

\bigskip
\bigskip
\bigskip


Requête 3 : Croissance démographique et Sécurité (LEFT JOIN)
\medskip

Langage naturel : Analyser l'indice de criminalité moyen dans les pays ayant un fort taux de natalité (plus de 25 naissances pour 1000 habitants).
\medskip

    SQL :
  
    SELECT country.country_name, country.birth_rate, AVG(city.crime_index) AS crime_moyen
    FROM country
    LEFT JOIN city ON country.country_name = city.country_name
    WHERE country.birth_rate > 25
    GROUP BY country.country_name, country.birth_rate;





![Requête_3](R3.png){#uml width="5cm" height="7cm"}
  
  \medskip
  
  Interpretation  :
    
Les résultats obtenus montrent que les pays présentant un taux de natalité supérieur à 25 naissances pour 1000 habitants sont exclusivement des pays en développement, principalement situés en Afrique subsaharienne et en Asie du Sud. On observe que la majorité de ces pays affiche également un indice de criminalité moyen élevé, avec des valeurs particulièrement marquées pour l'Afghanistan (79.8), Papua New Guinea (80.7) et la Namibie (68.6). Ces résultats suggèrent qu'une forte natalité tend à s'accompagner d'une insécurité urbaine plus importante. Cependant, il convient de nuancer cette observation : la natalité élevée n'est pas une cause directe de la criminalité, mais constitue plutôt un indicateur de sous-développement économique, qui va de pair avec d'autres facteurs tels que la pauvreté, le chômage ou la faiblesse des institutions. Par ailleurs, certains pays comme le Pakistan (43.0) ou l'Égypte (47.25) présentent un taux de natalité élevé mais un indice de criminalité plus modéré, ce qui confirme que le lien entre les deux variables n'est pas mécanique. Enfin, le recours au LEFT JOIN garantit que tous les pays à fort taux de natalité sont inclus dans les résultats, même ceux pour lesquels aucune ville n'est référencée dans la base.

\bigskip
\bigskip
\bigskip

Requête 4 : Contraste Salaire Minimum / Sécurité (RIGHT JOIN + IS NOT NULL)
\medskip

Langage naturel : Comparer le salaire minimum des pays pour les villes aux deux extrêmes de sécurité (crime > 70 ou crime < 30), en ignorant les pays sans salaire minimum officiel.
\medskip

    SQL :
  
    SELECT country.country_name, country.minimum_wage, city.city_name, city.crime_index
    FROM city
    RIGHT JOIN country ON city.country_name = country.country_name
    WHERE country.minimum_wage IS NOT NULL
    AND (city.crime_index > 70 OR city.crime_index < 30);





![Requête_4](R4.png){#uml width="5cm" height="6cm"}
  
  \medskip
  
Interpretation  :
    
résultats obtenus mettent en évidence un constat paradoxal : un salaire minimum élevé ne garantit pas nécessairement une faible criminalité urbaine. En effet, l'Australie, qui affiche le salaire minimum le plus élevé du tableau (13.59), voit tout de même la ville d'Alice Springs apparaître avec un indice de criminalité de 74.8. De même, les États-Unis, avec un salaire minimum de 7.25, comptent plusieurs villes parmi les plus dangereuses du tableau, telles que Baltimore (75.5), Memphis (74.8) et Detroit (74.1). À l'inverse, des pays comme le Venezuela (0.01), l'Afghanistan (0.43) ou le Honduras (1.01) présentent les salaires minimums les plus bas et concentrent les villes les plus dangereuses, ce qui suggère tout de même une tendance générale : les pays les plus pauvres en termes de protection salariale tendent à enregistrer les indices de criminalité les plus élevés. Le filtre IS NOT NULL est ici essentiel, car il permet d'exclure les pays ne disposant pas de salaire minimum légal officiel, dont les données auraient faussé la comparaison. On peut donc conclure que le salaire minimum constitue un indicateur partiel de sécurité : il reflète un contexte économique général, mais ne suffit pas à lui seul à expliquer le niveau de criminalité d'une ville.

\bigskip
\bigskip
\bigskip

Requête 5 : Analyse des écarts de sécurité par pays
\medskip

Langage naturel : Afficher le PIB et le salaire minimum de chaque pays, avec l'indice de crime de leur ville la plus sûre et de leur ville la plus dangereuse.  
\medskip

    SQL :

     SELECT country.country_name, country.gdp, country.minimum_wage, MIN(city.crime_index) AS crime_min, MAX(city.crime_index) AS crime_max 
     FROM city 
     INNER JOIN country ON city.country_name = country.country_name 
     WHERE country.minimum_wage IS NOT NULL 
     GROUP BY country.country_name, country.gdp, country.minimum_wage;                     





![Requête_5](R5.png){#uml width="6cm" height="5cm"}

\medskip

Interpretation  :

D'un côté, dans les pays très pauvres (comme l'Afghanistan), l'insécurité est élevée partout : même la ville la plus "calme" reste dangereuse. Cela montre que la pauvreté généralisée empêche d'avoir des zones vraiment sûres.
D'un autre côté, dans les pays riches (comme l'Australie), on voit des écarts énormes. Une ville peut être très sûre (23) et une autre très dangereuse (74). Cela prouve que la richesse d'un pays peut créer des "bulles de sécurité", mais qu'elle ne protège pas toutes les villes de la même façon.
En résumé, un bon salaire minimum aide à faire baisser le crime, mais il ne suffit pas à rendre toutes les villes d'un pays égales face à l'insécurité. Nous utiliserons le logiciel R pour calculer plus précisément ce lien.

\bigskip
\bigskip
\bigskip

Requête 6 : Éducation supérieure et sécurité (Sous-requête)

\medskip

Langage naturel : Sélectionner les villes situées dans des pays dont le taux d'éducation supérieure est au-dessus de la moyenne mondiale de notre base.
\medskip

    SQL :
  
    SELECT city_name, crime_index
    FROM city
    WHERE country_name IN (
        SELECT country_name
        FROM country
        WHERE country.tertiary_ed_enrolment_pct > (SELECT AVG(country.tertiary_ed_enrolment_pct) FROM country)
    );




![Requête_6](R6.png){#uml width="3cm" height="7cm"}
  
  \medskip
  
Interpretation  :
    
L’analyse de ces résultats montre que l’investissement d’un pays dans l’enseignement supérieur n'entraîne pas automatiquement une baisse de la criminalité urbaine. En isolant les pays situés au-dessus de la moyenne mondiale en éducation, on observe des situations très contrastées. D’un côté, des villes comme Rosario (75.20) ou Alice Springs (74.80) conservent des indices de criminalité très élevés malgré un contexte national fortement diplômé. Cela prouve que l'instruction ne peut pas, à elle seule, compenser des problématiques locales comme les inégalités de revenus ou les tensions sociales.
À l’inverse, des exemples comme Vienne (26.90) ou Canberra (23.20) confirment qu’un haut niveau d’étude accompagne souvent une grande sécurité publique. Cette disparité souligne que le taux de scolarisation est une variable nationale qui ne reflète pas toujours la réalité complexe d'une ville précise. En conclusion, si l’accès aux études supérieures est un indicateur de développement majeur, il ne constitue pas une solution miracle contre la délinquance. La sécurité d'une métropole dépend d'un équilibre entre plusieurs facteurs et ne peut se résumer au seul niveau de diplôme de la population.

\bigskip
\bigskip
\bigskip


Requête 7 : Le contraste Richesse (PIB) / Sécurité (HAVING + ORDER BY + Jointure classique)
\medskip

Langage naturel : Lister les villes ayant un indice de criminalité critique (> 70) avec le taux de chômage du pays correspondant.
\medskip

    SQL :

    SELECT city.city_name, city.crime_index, country.unemployment_rate 
    FROM city 
    INNER JOIN country ON city.country_name = country.country_name 
    WHERE city.crime_index > 70;            





![Requête_7](R7.png){#uml width="4cm" height="8cm"}

\medskip

Interpretation  :

Les résultats obtenus permettent de dégager plusieurs observations intéressantes quant au lien entre population urbaine et criminalité moyenne. Tout d'abord, on remarque que le Venezuela affiche la criminalité moyenne la plus élevée de l'échantillon avec un indice de 83,60, malgré une population urbaine relativement modeste de 25 millions d'habitants, ce qui suggère que la taille de la population urbaine n'est pas à elle seule un facteur déterminant. Dans le même sens, l'Afrique du Sud présente un indice moyen de criminalité très élevé (78,84) pour une population urbaine de 39 millions, tandis que la Chine, dont la population urbaine est la plus massive de l'échantillon avec près de 843 millions d'habitants, affiche l'un des indices de criminalité les plus bas avec 28,34. Ce constat est également valable pour le Japon (28,85) et la Corée du Sud (24,70), deux pays très urbanisés mais caractérisés par une criminalité faible. À l'inverse, des pays comme le Brésil (69,26), l'Argentine (66,57) ou le Nigéria (67,50) combinent une population urbaine importante et une criminalité élevée. Ces résultats indiquent donc que la densité urbaine seule n'explique pas la criminalité, et que d'autres facteurs structurels tels que les inégalités économiques, la gouvernance ou le développement humain jouent un rôle tout aussi déterminant.

\bigskip
\bigskip
\bigskip


Requête 8 : Classement des pays les plus dangereux par rapport à la moyenne mondiale 

\medskip

Langage naturel : Sélectionner les pays dont l'indice de criminalité moyen est strictement supérieur à la moyenne mondiale de toutes les villes de la base, classés par dangerosité décroissante.  
\medskip

    SQL :

     SELECT country_name, AVG(crime_index) AS crime_moyen_pays
     FROM city
     GROUP BY country_name
     HAVING AVG(crime_index) > (SELECT AVG(crime_index) FROM city)
     ORDER BY crime_moyen_pays DESC;                   





![Requête_8](R8.png){#uml width="4cm" height="8cm"}

\medskip

Interpretation  :

Cette requête est cruciale pour notre étude car elle définit mathématiquement le seuil de "dangerosité". Au lieu de fixer arbitrairement une limite à 70, nous utilisons une sous-requête pour calculer la moyenne globale en temps réel.
Le résultat (voir capture) isole les pays qui tirent la moyenne mondiale vers le haut. On y retrouve en tête le Venezuela (83.6), la Papouasie-Nouvelle-Guinée (80.7) et le Honduras (80.5).
D'un point de vue statistique, ces pays représentent nos "points de vigilance". Cette liste nous permet d'identifier les zones où les politiques de sécurité publique semblent les plus inefficaces ou les plus instables, fournissant ainsi une base solide pour notre future analyse de corrélation sur R avec les indicateurs économiques.



## Quelques détails techniques


On peut interagir avec une base de données directement depuis RMarkdown : i.e. requêter puis récupérer et afficher le résultat directement depuis le .Rmd. Un fichier connexionBDD.Rmd est fourni pour donner des exemples.

# Matériel et Méthodes

## Logiciels

Pour la réalisation de ce projet, nous avons mobilisé un ensemble d'outils collaboratifs et techniques essentiels au bon déroulement de notre flux de travail. La communication interne au groupe ainsi que le partage immédiat des fichiers ont été centralisés sur Discord, Gmail et Google Drive. Concernant la gestion technique de la base de données, nous avons utilisé l'environnement MAMP afin d'assurer l'hébergement local, complété par phpMyAdmin pour l'administration SQL. 
\medskip

La phase de manipulation des données brutes s'est déroulée sur Excel et LibreOffice Calc, tandis que la production finale du rapport et l'intégration des analyses statistiques ont été effectuées directement sous RMarkdown.

\bigskip




## Description des Données

Notre étude s'articule autour de deux sources de données principales qui constituent le socle de notre base relationnelle. Le premier fichier, nommé crime-index-2023_clean.csv, regroupe 404 lignes détaillant les indices de criminalité à l'échelle des villes pour un poids total de 11 Ko.
\medskip

Le second fichier, world-data-2023-sql.csv, compile sur 103 lignes les indicateurs socio-économiques nationaux pour un poids de 12 Ko. Ces deux tables ont été structurées de manière à permettre des jointures précises, facilitant ainsi le croisement entre les réalités urbaines et les indicateurs macro-économiques mondiaux.
\bigskip

## Nettoyage des données 

Le nettoyage des données a représenté une étape fondamentale de notre travail de préparation sous Excel afin de garantir la parfaite cohérence des futures jointures. Pour la table consacrée aux villes, nous avons appliqué la fonction SUPPRESPACE pour uniformiser les noms de pays et éliminer les espaces parasites qui auraient pu bloquer les requêtes. 
\medskip

Nous avons également procédé au regroupement des États américains et des provinces canadiennes sous les dénominations uniques United States et Canada via l'outil de remplacement global. Enfin, nous avons pris soin de retirer les pays absents de notre base de référence mondiale, tels que l'Irlande, Porto Rico ou Taïwan. 
\medskip

  Concernant la table des pays, le tri a été effectué pour ne conserver que les nations possédant au moins une ville correspondante dans notre base de criminalité, en utilisant la fonction NB.SI. Les colonnes jugées non pertinentes pour notre problématique ont été systématiquement supprimées, tout comme les pays présentant un volume de données manquantes trop important, à l'image de la Corée du Nord. 
\medskip
  
  Une attention particulière a été portée au traitement du salaire minimum : nous avons choisi de maintenir les valeurs nulles pour des pays comme la Suisse ou le Danemark, car cette donnée traduit une réalité juridique précise, à savoir l'absence de salaire minimum légal, et ne constitue en aucun cas une erreur de saisie.
\bigskip

## Étapes de Pré-traitements

En amont de l'importation SQL, plusieurs étapes de pré-traitement ont été nécessaires pour adapter les fichiers aux contraintes du langage de requête et des calculs statistiques. Nous avons procédé à un formatage numérique rigoureux en supprimant les symboles parasites tels que le signe dollar ou le pourcentage, ainsi que les virgules servant de séparateurs de milliers dans les colonnes liées au PIB, à la population ou au chômage.
\medskip

Cette transformation est indispensable pour que SQL reconnaisse ces champs comme des types BIGINT ou FLOAT, autorisant ainsi les calculs de moyennes. Par ailleurs, nous avons standardisé les séparateurs décimaux en remplaçant la virgule par le point et substitué les cellules vides par le mot-clé NULL pour éviter toute erreur de type lors de l'intégration en base de données.
\bigskip

## Modélisation statistique

La phase finale de modélisation statistique s'appuie sur une approche combinant visualisation spatiale et analyse de corrélation sous l'environnement R. Nous avons d'abord généré une variable spécifique calculant l'indice de criminalité moyen par pays afin de produire une cartographie mondiale permettant une lecture immédiate des zones de tension. Cette visualisation est complétée par la réalisation de quatre graphiques de dispersion mettant en relation ce crime moyen avec le PIB, le salaire minimum, le taux de chômage et la population urbaine.
\medskip
  
  Enfin, nous effectuons des tests de corrélation linéaire afin de vérifier statistiquement si la combinaison de ces différents indicateurs exerce un impact significatif sur le niveau de sécurité des pays étudiés dans notre échantillon.


# Analyse Exploratoire des Données



## Utiliser R {.fragile}



\begin{figure}

{\centering \includegraphics[width=11cm]{rapport-GAMAI_files/figure-latex/unnamed-chunk-1-1} 

}

\caption{\label{fig:boxplots}Carte des indices de criminalité}\label{fig:unnamed-chunk-1}
\end{figure}


Carte mondiale du niveau de sécurité
Cette carte du monde représente l'indice moyen de criminalité par pays, avec une échelle de couleurs allant du jaune (indice faible, environ 20) au violet foncé (indice élevé, environ 80). On constate que les pays d'Amérique du Sud et d'Afrique sub-saharienne présentent les indices de criminalité les plus élevés, tandis que l'Europe et une partie de l'Asie affichent des niveaux plus faibles. Les pays en gris correspondent à des données non disponibles. Cette visualisation confirme que la criminalité est un phénomène inégalement réparti à l'échelle mondiale et fortement lié aux contextes géographiques et économiques régionaux.





Les lignes de code ne doivent pas dépasser dans la marge de droite. Ainsi on pourrait remplacer le chunk ci-dessous:

\begin{figure}

{\centering \includegraphics[width=9cm]{rapport-GAMAI_files/figure-latex/unnamed-chunk-2-1} 

}

\caption{PIB et indice de criminalité}\label{fig:unnamed-chunk-2}
\end{figure}

Nuage de points entre le PIB et l'indice de criminalité
Dans ce nuage de points, nous distinguons deux ensembles distincts. La grande majorité des pays se concentre à gauche du graphique, avec un PIB proche de zéro à l'échelle considérée, et des indices de criminalité très variables entre 15 et 85. En revanche, à l'extrémité droite apparaissent quelques points isolés correspondant à des pays avec un PIB très élevé, dont un point notable autour de 2.0e+13 avec un indice de criminalité modéré d'environ 53. Cette concentration suggère que les pays à très fort PIB sont peu nombreux mais se distinguent clairement des autres. On pourrait supposer que ces points correspondent aux États-Unis ou à la Chine, dont le PIB est nettement supérieur aux autres nations.





par celui-ci:

\tiny

\begin{figure}

{\centering \includegraphics[width=9cm]{rapport-GAMAI_files/figure-latex/unnamed-chunk-3-1} 

}

\caption{Salaire minimum et indice de criminalité}\label{fig:unnamed-chunk-3}
\end{figure}

Nuage de points entre le salaire minimum et l'indice de criminalité
Ce nuage de points présente une dispersion importante des données sur l'ensemble de la plage des salaires minimums. On remarque toutefois une tendance légèrement décroissante : les pays ayant un salaire minimum plus élevé tendent à avoir un indice de criminalité plus faible. Cette observation est cohérente avec l'idée qu'un niveau de vie plus élevé contribuerait à réduire la criminalité. Néanmoins, la dispersion reste importante, ce qui indique que d'autres facteurs entrent également en jeu.





\normalsize

\begin{figure}

{\centering \includegraphics[width=9cm]{rapport-GAMAI_files/figure-latex/unnamed-chunk-4-1} 

}

\caption{Taux de chomage et indice de criminalité}\label{fig:unnamed-chunk-4}
\end{figure}

Nuage de points entre le taux de chômage et l'indice de criminalité
Dans ce nuage de points, nous observons une légère tendance positive entre le taux de chômage et l'indice de criminalité. En effet, les pays présentant un taux de chômage élevé, autour de 20-25%, semblent avoir des indices de criminalité plus élevés. Cependant, cette tendance reste peu marquée car de nombreux pays avec un faible taux de chômage affichent également des indices de criminalité élevés. On ne peut donc pas conclure à une corrélation forte entre ces deux variables à partir de ce seul graphique.






\begin{figure}

{\centering \includegraphics[width=9cm]{rapport-GAMAI_files/figure-latex/unnamed-chunk-5-1} 

}

\caption{Population urbaine et indice de criminalité}\label{fig:unnamed-chunk-5}
\end{figure}


Nuage de points entre la population urbaine et l'indice de criminalité
Nous pouvons observer dans ce nuage de points une dispersion assez homogène des données sur l'ensemble du graphique. Les points sont répartis sur toute la plage de l'axe des abscisses, qui suit une échelle logarithmique allant de 100K à 1B habitants urbains, sans qu'une tendance claire ne se dégage. L'indice moyen de criminalité reste globalement compris entre 20 et 80 quelle que soit la taille de la population urbaine. Cela suggère que la population urbaine n'a pas d'influence linéaire directe et significative sur l'indice de criminalité.






# Inférence statistique et modélisation



## Modélisation statistique : La Régression Linéaire Multiple


\bigskip


Dans cette partie, nous cherchons à savoir si le niveau de sécurité d'un pays est influencé par la combinaison de plusieurs facteurs économiques : le PIB, le salaire minimum et le taux de chômage.

\medskip

En cours, nous avons appris à tester la liaison entre deux variables (corrélation simple). Cependant, notre problématique nécessite d'analyser l'impact de trois variables en même temps. Comme cette méthode n'a pas été abordée en cours, nous avons, sur les conseils de notre professeure, effectué des recherches sur internet et utilisé des outils d'intelligence artificielle pour identifier la procédure statistique adaptée. Nos recherches nous ont conduits à utiliser la Régression Linéaire Multiple et son test de significativité globale.

\bigskip

Étape 1 : Formulation des hypothèses
\medskip

Nous voulons savoir si notre modèle économique global a un sens.

    H0 : La criminalité est indépendante des variables choisies 
    (les coefficients de liaison sont tous nuls).
    H1 : Au moins une des variables (PIB, salaire ou chômage) 
    a un impact significatif sur la criminalité.

\bigskip

Étape 2 : Calcul de la statistique de test
\medskip

Pour tester plusieurs variables simultanément, la statistique utilisée n'est plus le coefficient de corrélation r, mais la statistique de Fisher (notée F).
Cette valeur, calculée par le logiciel R, mesure si la part d'explication apportée par nos trois variables est suffisamment importante par rapport à l'erreur du modèle. Plus cette valeur F est élevée, plus le lien entre l'économie et le crime est probable.
\bigskip

Étape 3 : Détermination de la p-value
\medskip

Grâce à la fonction summary(lm(...)) sur R, nous obtenons directement les résultats de ce test global sans avoir à utiliser de table de lecture complexe :

    Valeur de la statistique F : 2.982
    p-value globale : 0.03637
    
\bigskip

Étape 4 : Règle de décision et interprétation
\medskip

Nous utilisons le seuil de risque habituel de 5% (0,05).
La règle de décision est la suivante : si la p-value est inférieure à 0,05, nous rejetons l'hypothèse d'absence de lien.
Ici, 0,036 < 0,05. Nous rejetons donc H0​.

Conclusion du test : Nous pouvons affirmer, avec un risque d'erreur de 5%, que la combinaison du PIB, du salaire minimum et du chômage influence significativement le niveau de criminalité d'un pays.
5.1 Analyse des résultats du modèle

\bigskip

L'examen détaillé des résultats nous permet d'affiner cette conclusion :

    Un impact réel mais partiel (R2) : Le coefficient de détermination est 
    de 0.1029. Cela signifie que notre modèle explique environ 10,3 % des 
    variations de la criminalité. C'est un résultat significatif, mais qui
    montre que l'économie n'est qu'un facteur parmi d'autres 
    (comme la politique ou l'éducation).

    L'importance cruciale du salaire minimum : En regardant les résultats 
    pour chaque variable, nous remarquons que seul le Salaire Minimum a 
    une influence propre vraiment significative (p=0,019). Son coefficient 
    est négatif (-1,23), ce qui prouve que plus le salaire minimum augmente,
    plus la criminalité baisse.

    Le rôle secondaire du PIB et du chômage : Curieusement, une fois que l'on 
    prend en compte le salaire, le PIB et le chômage ne semblent plus avoir 
    d'impact direct important sur le crime dans notre modèle.

Synthèse : Ce test nous permet de conclure que pour améliorer la sécurité, agir sur le niveau de rémunération de base (salaire minimum) semble être un levier plus efficace que la simple recherche de croissance économique (PIB).



```
## 
## Call:
## lm(formula = CrimeIndex_Moyen ~ GDP + Minimum.wage + Unemployment.rate, 
##     data = data_propre)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -32.988 -10.520  -0.673  11.322  33.930 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)    
## (Intercept)        4.694e+01  3.637e+00  12.905   <2e-16 ***
## GDP               -2.346e-13  5.285e-13  -0.444    0.658    
## Minimum.wage      -1.234e+00  5.152e-01  -2.395    0.019 *  
## Unemployment.rate  5.160e-01  4.016e-01   1.285    0.203    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.16 on 78 degrees of freedom
## Multiple R-squared:  0.1029,	Adjusted R-squared:  0.06838 
## F-statistic: 2.982 on 3 and 78 DF,  p-value: 0.03637
```




# Discussion

Notre base de données présente un déséquilibre géographique notable : les États-Unis représentent près de la moitié des villes étudiées, tandis que certaines régions comme l'Afrique subsaharienne ou l'Asie centrale sont sous-représentées. Ce biais limite la portée de nos conclusions à l'échelle mondiale. Élargir la collecte de données à d'autres zones géographiques permettrait d'améliorer la généralisation de nos résultats et de mieux comprendre si les tendances observées se vérifient dans d'autres contextes culturels et économiques.


# Conclusion et perspectives {.label:ccl}

Conclusions principales
Notre étude visait à comprendre dans quelle mesure le mode de développement d'un pays — urbanisation, économie et géographie — influence le niveau de sécurité de ses villes. Les analyses menées sur plus de 400 villes et une centaine de pays nous permettent de tirer plusieurs conclusions.
\medskip

Premièrement, la richesse brute d'un pays, mesurée par son PIB, ne garantit pas automatiquement la sécurité. Des nations économiquement puissantes comme le Venezuela ou l'Afrique du Sud affichent des niveaux de criminalité très élevés, tandis que d'autres comme le Qatar ou la Suisse combinent richesse et tranquillité.
\medskip

Deuxièmement, notre modèle statistique indique que le salaire minimum semble être un facteur favorable à la réduction de la criminalité. En règle générale, les pays qui garantissent un revenu minimum plus élevé tendent à afficher des indices de criminalité plus faibles. Cependant, cette tendance n'est pas absolue : des pays comme l'Australie possèdent un salaire minimum élevé mais connaissent tout de même des zones où la criminalité reste importante.
\medskip

Troisièmement, ni l'urbanisation massive ni la densité de population ne semblent être des facteurs automatiques d'insécurité. Des mégapoles asiatiques comme celles du Japon ou de la Chine restent très sûres malgré leur forte concentration démographique.
\bigskip

Recommandations :

Pour les décideurs publics souhaitant améliorer la sécurité urbaine, nos résultats suggèrent de ne pas se concentrer uniquement sur la croissance économique brute. L'amélioration des conditions de vie de base, notamment par des salaires décents et l'accès aux services publics, pourrait constituer un levier intéressant. L'urbanisation rapide ne doit pas être perçue comme une fatalité criminogène : avec une bonne planification, les grandes villes peuvent rester sûres.
\bigskip

Perspectives à court terme :

Il serait utile d'enrichir notre modèle en ajoutant des variables supplémentaires qui mesurent les inégalités de revenus ou le niveau d'éducation dans chaque pays. Cela permettrait peut-être d'expliquer une plus grande part de la criminalité, car notre modèle actuel n'en explique qu'environ 10%.
Il serait également pertinent de croiser nos données avec des statistiques officielles de criminalité, comme les taux d'homicides ou les vols déclarés par les autorités, afin de valider notre indice basé sur des perceptions subjectives.
\bigskip

Perspectives à long terme :

D'un point de vue méthodologique, il serait intéressant d'analyser l'évolution de la criminalité sur plusieurs années plutôt qu'une seule année de données (2023). Cela permettrait de voir si les tendances observées se confirment dans le temps et si certains pays connaissent des améliorations ou des dégradations de leur sécurité.
Du point de vue du domaine de la sécurité urbaine, il pourrait être pertinent d'étudier l'impact de politiques publiques spécifiques sur la criminalité. Par exemple, analyser ce qui se passe lorsqu'un pays augmente son salaire minimum ou met en place des programmes sociaux pourrait aider à mieux comprendre les leviers d'action concrets.
\bigskip

Difficultés rencontrées :
\medskip

Partie Bases de Données :

Plusieurs difficultés techniques ont été rencontrées lors de la gestion de notre base de données. Le nettoyage et l'uniformisation des données ont représenté un travail considérable : suppression d'espaces parasites, regroupement des États américains et provinces canadiennes, suppression de pays absents dans l'une des deux tables. La gestion des valeurs manquantes a également posé problème, notamment pour le salaire minimum qui n'existe pas dans certains pays. Enfin, l'importation dans phpMyAdmin a nécessité de nombreux ajustements techniques pour que les types de données soient correctement reconnus par SQL.
\bigskip

Partie Statistique :

Du côté statistique, le choix du bon modèle a été difficile. Nous souhaitions tester l'impact simultané de plusieurs variables économiques sur la criminalité, ce qui dépassait le cadre de la corrélation simple vue en cours. Le faible pouvoir explicatif du modèle (R² = 0.103) nous a montré que la criminalité dépend de nombreux facteurs non mesurés dans cette étude. Enfin, l'utilisation d'un indice de perception plutôt que de statistiques officielles constitue une limite méthodologique, car nous n'avons pas pu vérifier si les perceptions correspondaient bien à la réalité du terrain.



# Bibliographie {-}

Sources scientifiques : 
\medskip

Nelly Exbrayat, Victor Stephane. Does Urbanization Cause Crime? Evidence from Rural-Urban Migration in South Africa. 2024. ⟨halshs-04390026⟩. Disponible sur : https://shs.hal.science/halshs-04390026
\medskip

Sources de données :
\medskip

World Crime Index 2023. Dataset Kaggle. Disponible sur : https://www.kaggle.com/datasets/arsalanrehman/world-crime-index-2023
Global Country Information Dataset 2023. Dataset Kaggle. Disponible sur : https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023
\bigskip

Outils et méthodes
\medskip

Pour la partie statistique, nous avons principalement utilisé les connaissances acquises en cours de Sciences des Données 2. Cependant, pour la modélisation par régression linéaire multiple, méthode non abordée en cours, notre professeure nous a conseillé de faire des recherches complémentaires. Nous nous sommes notamment appuyés sur des outils d'intelligence artificielle (ChatGPT, Claude) pour comprendre le fonctionnement de cette méthode, interpréter correctement les résultats (coefficients, p-values, R²) et vérifier la validité de notre démarche statistique.

Par ailleurs, nous avons également utilisé l'intelligence artificielle comme aide à la rédaction pour améliorer la clarté de notre propos, corriger les fautes d'orthographe et de syntaxe, et formuler nos idées avec un vocabulaire adapté au niveau académique attendu. L'ensemble des analyses, requêtes SQL, traitements de données et interprétations des résultats ont cependant été réalisés par les membres de notre équipe.








