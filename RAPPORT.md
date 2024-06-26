**GHAZEL Hassen et HALVICK Thomas**


# 3 Etude “théorique” de cas simples (6.5 points) 


## 3.1 Influence de η

![alt text](img/formule1.png)


### Dans le cas où η = 0 quelle sera la prochaine valeur des poids du neurone gagnant ?


Si η = 0, alors nous avons :

![alt text](img/formule2.png)

Selon la formule ci-dessus, si η = 0, alors ∆wji = 0 : le poids d'aucun neurone ne sera mis à jour.
Par conséquent, la prochaine valeur des poids sera simplement égale à leur valeur courante et donc la valeur du neuronne gagnant restera inchangée.

### Même question dans le cas où η = 1.

Dans ce cas, on s'intéresse uniquement au neurone gagnant.
Donc j-j* = 0, et la formule devient :

![alt text](img/formule0.png)

*Donc nous avons :* 

![alt text](img/formule3.png) <br/>
![alt text](img/formule3.5.png)

Dans le cas où η = 1, la mise à jour des poids pour le neurone gagnant est maximale. 
De ce fait, la prochaine valeur pour le neurone gagnant sera égale a la valeur de l'entrée.

### Dans le cas où η ∈]0, 1[ (paramétrisation “normale”) où se situera le nouveau poids par rapport à W∗ et X en fonction de η (formule mathématique simple ou explication géométrique) ?

Si η est compris entre 0 et 1, le nouveau poids sera situé sur la droite reliant le poids courant W(t) et la valeur d'entrée X.
Le nouveau poids W(t+1) sera donné par :

![alt text](img/formule4.png)

Le déplacement le long de cette droite diffère donc selon la valeur de η.
Plus η est petit, plus le déplacement est faible, et plus le nouveau poids sera proche de W(t), mais plus η est grand, plus le déplacement sera important, et plus le nouveau poids s'éloignera de W(t) pour aller vers la valeur d'entrée.

Donc plus η est grand, plus le reseau apprendra vite, mais plus il y a de risque de ne pas converger vers la solution optimale. A l'inverse, plus η est petit, plus le reseau apprendra lentement, mais plus il y a de chance de converger vers la solution optimale.

### Que va-t-il se passer si η > 1 ?

Si η > 1, le taux d'apprentissage sera très élevé, et le nouveau poids sera situé au-delà de X.
De ce fait, l'ajustement du poids sera amplifié, ce qui signifie que le poids se déplacera plus rapidement vers la position de X.

## 3.2 Influence de σ

### Si σ augmente, les neurones proches du neurone gagnant (dans la carte), vont-ils plus ou moins apprendre l’entrée courante ?

![alt text](img/formule5.png)

Si σ augmente,alors l'exposant tends vers -0 et la formule ci-dessus va donc tendre vers 1. De ce fait, l'augmentation de σ va permettre de se rapprocher de plus en plus de la valeur d'entrée et de l'apprendre davantage.

### Si σ est plus grand, à convergence, l’auto-organisation obtenue sera-t-elle donc plus “resserrée” (i.e. une distance plus faible entre les poids des neurones proches) ou plus “lâche” ?

Si σ est plus grand, à convergence, l'auto-organisation obtenue sera plutôt resserrée.
Les points convergeant vers un seul et même poids, ils vont donc devenir de plus en plus proches, de plus en plus "serrés".

### Quelle mesure (formule mathématique qui sera à implémenter dans la section 4) pourrait quantifier ce phénomène et donc mesurer l’influence de σ sur le comportement de l’algorithme ?

Pour quantifier ce phénomène, il est possible de calculer la distance moyenne entre tous les poids des neurones de la carte.
Ainsi, plus la valeur de cette distance est faible, plus les neurones sont resserrés, et inversement.

![alt text](img/formule7.png)


## 3.3 Influence de la distribution d’entrée

Prenons le cas très simple d’une carte à 1 neurone qui reçoit deux entrées X1 et X2.

### Si X1 et X2 sont présentés autant de fois, vers quelle valeur convergera le vecteur du poids du neurone (en supposant un η faible - pour ne pas avoir à tenir compte de l’ordre de présentation des entrées - et suffisamment de présentations - pour négliger l’influence de l’initialisation des poids) ?

Dans le cas d'une carte à 1 neurone, le neurone traité sera toujours le neurone gagnant. Dans ce cas simple, la valeur du poids du neurone va converger vers la moyenne pondérée des valeurs d'entrée, c'est-à-dire ici `(X1 + X2) / 2`.

##### Processus de convergence
- **Taux d'apprentissage faible (η faible) :** Permet des ajustements progressifs des poids, favorisant une convergence stable.
- **Répétition des présentations des entrées :** Nécessaire pour négliger l'effet de l'initialisation des poids et assurer la convergence vers une valeur stable.

##### Explication
- La mise à jour du poids du neurone est proportionnelle à la différence entre l'entrée courante et le poids actuel.
- Si X1 et X2 sont présentés autant de fois, le poids du neurone se situera à équidistance entre les deux valeurs, soit `(X1 + X2) / 2`.

##### Remarque
L'ordre de présentation des entrées peut influencer la vitesse de convergence et la stabilité de l'apprentissage, mais avec un η faible, cet effet est atténué.

En résumé, avec un η faible et une répétition suffisante des présentations des données, les poids du neurone convergeront vers la moyenne pondérée des valeurs d'entrée, indépendamment de l'ordre de présentation des données.

### Même question si X1 est présenté n fois plus que X2.

Si X1 est présenté n fois de plus que X2, la convergence du vecteur de poids du neurone sera davantage influencée par X1 que par X2. 
De ce fait, le poids du neurone se rapprochera plus de la valeur de X1 que de X2. 

Le poids final restant une moyenne pondérée des valeurs de X1 et X2, le poids de X1 sera simplement n fois supérieur à celui de X2 et aura donc une plus grande importance dans la formule.

### Même question dans le cas d’entrées provenant d’une base de données quelconque. 

Dans ce cas précis, le poids du neurone dépendra de chaque entrée, notament au niveau des poids et des valeurs de chacune de ces entrées. Donc le poids final sera égal la moyenne pondérée de toutes les entrées.

### Reconsidérons maintenant le cas d’une carte avec plusieurs neurones en se focalisant sur un neurone quelconque. Quels exemples apprend ce neurone et avec quelle “force” ?

Dans ce cas précis, le neurone en question sera attiré par chaque exemple, mais de facon différente, selon la distance avec le neurone gagnant. Cela veut donc dire que plus le neurone en question sera proche du neurone gagnant, plus il sera attiré vers la valeur de l'entrée.


### En déduire comment vont se répartir les neurones d’une carte à plusieurs neurones recevant des données d’une base d’apprentissage en fonction de la densité des données. Pour rappel, la mesure de quantification vectorielle permet de mesurer ce phénomène.

Suivant les données en entrée, les neurones seront attirés à des dégrés divers et varié. Ils se distribueront pour couvrir l'ensemble des données en se concentrant près des zones les plus denses. Cela réduit la distance entre chaque donnée d'entrée et le neurone gagnant le plus proche.


# 4 Etude pratique

## 4.3 Analyse de l’algorithme
Pour chacune des grandeurs ci dessous, nous présenterons dans cette partie différents tests réalisés en faisant varier les paramètres observés (η, σ, N ...) afin de confronter nos observation réelles à notre étude théorique précédente. Pour ce faire, nous observerons l'erreur de quantification vectorielle, et la dispertion des poids, et suivant les différentes valeurs du paramètre étudié, nous stockerons dans le fichier excel `courbe.xlsx`, ces valeurs dans des tableaux, et nous afficherons dans notre analyse, les courbes correspondantes. De plus, nos valeurs par défaut sont *η = 0.05, σ = 1.4, N = 30000, grille = 10x10 et le jeu de données = numéro 1*. Donc, lorsque ne passerons de l'étude d'un paramètre à un autre, nous remetrons la valeur initial du paramètre observé précedement.

-   taux d’apprentissage η

<ins><b>hypothèse</b></ins>:  Selon nous, η va influer sur la capacité des neurones à apprendre des entrées, mais des valeurs trop basses ou trop élevées pourrait être néfaste à cet apprentissage.

![alt text](img/influence_eta.png)

<ins><b>résultat</b></ins>: On constate que plus le taux d’apprentissage η augmente, plus la dispertion des poids augmentes. Quant à l'erreur de quantification vectorielle (EQV), pour η = 0, EQV est grand. De plus, il est difficile de le voir sur la courbe, mais dans le fichier excel, plus η augmente, plus EQV augmente petit à petit.

En executant le code, nous avons aussi constaté que le taux d'apprentissage influe sur la disposition des neurones : très resserrée quand η est très bas, et au contraire moins resserés quand η dépasse 1. Enfin, la dispertion des poids semble à peu près stable quand η ∈ [0,05; 1] avec une valeur moyenne d'environ 0,883 dans cette intervalle.

-   largeur du voisinage σ

<ins><b>hypothèse</b></ins>:  Selon nous, σ influe sur la disposition des neurones sur la carte, c'est-à-dire s'ils seront plutôt resserrés entre eux ou non.

![alt text](img/influence_sigma.png)

<ins><b>résultat</b></ins>: Sur la courbe ci dessus, on constate que plus σ augmente, plus l'erreur de quantification vectorielle augmente également, mais plus la dispertion des poids diminue : les neurones se retrouvent davantage resserrés.

L'idéal serait alors ici de choisir une valeur ni trop élevée ni trop basse pour σ, permettant de diminuer l'erreur de quantification vectorielle, tout en conservant une structure assez resserrée. Donc, sur la courbe on voit que le point d'absice σ où la dispertion et l'erreur de quantification se croise, est à σ = 6.


-   nombre de pas de temps d’apprentissage N

<ins><b>hypothèse</b></ins>:  Selon nous, N est lié à la qualité de l'apprentissage des neurones, c'est-à-dire, que plus N sera grand, plus les neurones auront le temps d'apprendre, et plus leur disposition se stabilisera.

![alt text](img/influence_N.png)

<ins><b>résultat</b></ins>: Sur la courbe, et après avoir éxecuté notre code pour différente valeur de N, nous avons constaté que plus le temps d'apprentissage est élevé, et plus les neurones vont pouvoir apprendre, ce qui entraîne une baisse significative de l'erreur de quantification vectorielle.
Cependant, l'auto-organisation semble se stabiliser dès N = 2500, avec une dispertion des poids plutot élevé (environ 0,87).

Il nous apparaît donc évident de choisir une valeur de N supérieure à ce seuil de stabilisation, puisque la disposition des neurones ne changera pas davantage, mais qui permettra de baisser encore quelque peu l'erreur de quantification vectorielle.

-   taille et forme de la carte

<ins><b>hypothèse</b></ins>:  Selon nous, plus la carte sera grande, et plus les neurones pourront prendre de la place, entraînant ainsi un relâchement dans leur disposition interne.

![alt text](img/influence_taille_forme.png)

<ins><b>résultat</b></ins>: Plus la taille de la carte augmente, plus l'erreur de quantification vectorielle diminue, et plus la disposition des neurones est lâche.
On remarque cependant que inversement, plus la taille de l'image augmente plus la dispertion des poids va augmenter.

Le choix de la carte va se faire selon ce que nous souhaitons représenter et en accord avec le problème à résoudre, selon le fait que nous voulons accorder de l'importance à EQV ou la dispertion des poids. A partir de `10x10`, on constate que la dispertion des poids est à 0.828, et elle augmente, mais petit à petit. Néanmoins, EQV est très faible (0.0255). Donc nous pourrions gardé cette valeur de `10x10`. 



-   jeu de données

<ins><b>hypothèse</b></ins>:  Selon nous, les jeux de données vont influer sur la disposition des neurones sur la carte, étant donné que les dispositions des données d'entrée seront différentes. 


| Numéro du jeu de données | Jeu de données                                     | Erreur de quantification vectorielle | Dispertion des poids |
|--------------------------|----------------------------------------------------|--------------------------------------|----------------------|
| **1**                    | ![Jeu de données 1](img/jeu_de_données_1.png)      | 0,019538320                          | 0,878051739          |
| **2**                    | ![Jeu de données 2](img/jeu_de_données_2.png)      | 0,019072294                          | 0,804402386          |
| **3**                    | ![Jeu de données 3](img/jeu_de_données_3.png)      | 0,014898156                          | 0,785508665          |
| **4**                    | ![Jeu de données 4](img/jeu_de_données_4.png)      | 0,008491655                          | 0,597403228          |

## <ins>Pour le jeu de données 1</ins> 

<ins><b>hypothèse</b></ins>: les données sont uniformément réparties dans l'espace <br/>

<ins><b>résultat</b></ins>: on peut voir ci-dessous que les données forme une sorte de carré, lié aux données d'entrée uniformément réparties dans l'espace.

![alt text](img/jeu_de_données_fin_1.png)

## <ins>Pour le jeu de données 2</ins> 

<ins><b>hypothèse</b></ins>: les données sont réparties de manière uniforme dans les 3/4 de l'espace, sauf dans le coin en haut à droite qui sera vide ou peu dense <br/>

<ins><b>résultat</b></ins>: on peut voir ci-dessous que l'on constate un comportement un peu similaire que pour le jeu 1. Cependant, on peut remarquer que le côté en haut à droite semble être évité. Ce comportement est lié aux données d'entrée fournies, car ces dernières ne sont pas présentes sur le coin haut droit.

![alt text](img/jeu_de_données_fin_2.png)

## <ins>Pour le jeu de données 3</ins> 

<ins><b>hypothèse</b></ins>: les données sont réparties de manière uniforme dans les 2/4 de l'espace, sauf dans le coin en haut à droite et le coin en bas à gauche qui seront vide ou peu dense <br/>

<ins><b>résultat</b></ins>:  on peut voir ci-dessous que le côté en haut à droite et le côté en bas à gauche sont aussi évités. Ceci est de nouveau lié à une absence de données d'entrée fournies. Cette fois-ci, il manque données d'entrée sur le côté bas gauche, le côté haut droit


![alt text](img/jeu_de_données_fin_3.png)

## <ins>Pour le jeu de données 4</ins>

<ins><b>hypothèse</b></ins>: les données sont réparties de manière a recouvrir au maximum les données d'entrée<br/>

<ins><b>résultat</b></ins>: on peut voir ci-dessous que les poids des neurones sont bien plus resserrés que dans les zone où la donnée est plus dense.

![alt text](img/jeu_de_données_fin_4.png)

*Ainsi, selon le problème à traiter, il faudra donc bien choisir ses données d'entrée afin de s'assurer le meilleur apprentissage (et le plus adapté à la problématique) pour les neurones.*


- La topologie de la carte (hexagonale)

<ins><b>hypothèse</b></ins>: la topologie de la carte va influer sur la disposition des neurones, et donc sur leur apprentissage. Ainsi les liaisons entre les neurones devraient être de forme triangulaire et former un réseau hexagonal. <br/>

<ins><b>résultat</b></ins>: En changeant la topologie de la carte les poids des neuronnes se repartissent différemment en suivan la topologie de la carte.

![alt text](img/topologie_hexagone.png)

## 4.4 Bras robotique

Afin de retrouver la predire la position qu’aura le bras ́etant donne une position motrice il suffit juste de prendre le neuronne gagnant, et de prendre en compte que les 2 premiers poids du neuronne. 
Ainsi, on peut retrouver la position motrice du bras en recuperant les 2 derniers poids du neuronne gagnant.

Pour predire la position motrice ́etant donne une position spatiale il faut aussi prendre le neuronne gagnant mais prendre en compte que les 2 derniers poids du neuronne
Ainsi, on peut retrouver la position spatiale du bras en recuperant les 2 premiers poids du neuronne gagnant.

Afin de prédire la suite des positions du bras, il suffit de tracer une droite entre les deux positions motrices et de la parcourir en en prenant des points intermédiaires où le neuronne gagnant change. 
Ainsi on peut prédire la suite des positions du bras en fonction des neurones gagnants et des poids associés.
![alt text](img/robot.png)