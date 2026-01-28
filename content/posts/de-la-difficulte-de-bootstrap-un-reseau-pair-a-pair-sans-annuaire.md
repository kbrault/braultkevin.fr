+++
date = '2025-12-29'
title = 'De la difficulté de bootstrap un réseau pair à pair sans annuaire'
categories = ['Maths', 'Computer Science', 'Computer Network']
+++

Dans un réseau centralisé, la découverte des pairs est facilitée par un annuaire ou une autorité centrale. Cependant, ce modèle crée un point de défaillance unique. Pour un réseau dont l'objectif est de contourner la censure, un serveur central est une cible facile : une fois l'adresse IP de l'annuaire bloquée par un État ou une autorité, l'intégralité du réseau devient invisible. Le but de la décentralisation totale est de rendre la découverte de pairs aussi résiliente que le réseau lui-même.

Un réseau entiérement décentralisé ne repose plus sur une autorité centrale et délègue la découverte des noeuds ... aux noeuds eux même. Mais la capacité d'un noeud à en découvrir un autre sans intermédiaire repose sur deux facteurs critiques : l'immensité de l'espace d'adressage et la stabilité temporelle des hôtes.

Dans le cadre d'un réseau IPv4, l'espace d'adressage global est défini par l'ensemble des vecteurs binaires de dimension 32 :

$${A} = \{0, 1\}^{32}$$

La cardinalité de cet espace, représentant le nombre total d'adresses adressables est : 

$$\lvert A \rvert = 2^{32} = 4\,294\,967\,296$$

Soit $n$ le nombre de noeuds actifs appartenant au réseau distribué à un instant $t$, on définit la densité du réseau $\delta$ comme la probabilité qu'une adresse échantillonnée de manière aléatoire uniforme appartienne à l'ensemble des pairs actifs du réseau : 

$$\delta = \frac{|A|}{n}$$

La recherche d'un pair par échantillonnage aléatoire uniforme peut être modélisée par une loi géométrique ou chaque requête est une épreuve de Bernouli indépendant de paramètre $p=\delta$. L’espérance mathématique notée ${E}[X]$ du nombre de requêtes nécessaires pour établir le premier contact est donc définie par :

$${E}[X] = \frac{1}{\delta} = \frac{2^{32}}{n}$$

Pour un réseau en phase de démarrage avec $n=100$ pairs, nous obtenons : 

$${E}[X] = \frac{4\,294\,967\,296}{100} \approx 4{,}29 \times 10^{7} { requetes}$$

Considérons maintenant $v$ la vitesse de balayage (nombre de scans sur l'espace d'adressage), le temps moyen de découverte $T$ est exprimé par :

$$T = \frac{{E}[X]}{v} = \frac{A}{n \cdot v}$$

Supposons une capacité de scan optimiste de $v=10^3$ requêtes par seconde : 

$$T = \frac{4\,294\,967\,296}{1000 \cdot 100} \approx 42\,949 \text{ secondes} \approx 11,93 \text{ heures}$$

Ainsi la découverte par force brute d'un noeud du réseau sans autorité est de prêt de 12 heures, et ce, pour un réseau déjà existant de 100 pairs.

Pour un réseau de seulement $n=2$ pairs, le temps de découverte théorique serait d'environ 25 jours. Sur un réseau d'adresse IPv6, on parle de $5,4 \times 10^{18} \text{milliards d’années}.$

La durée d'un bail DHCP n'est pas fixe et peu varier selon les constructeurs de routeurs, du fournisseur d'accès internet et du type de réseau. On peut faire une approximation rapide en parlant d'un bail de 7 à 14 jours en moyenne. 

Prenons $T$ la durée maximum de 14 jours (soit 1209600 secondes), le nombre total de requêtes qu'un pair peut envoyer pour en découvrir un autre est :

$$
n = v \times T = 10^3 \times 1\,209\,600 = 1{,}2096 \times 10^9 \text{ tentatives}
$$

Chaque tentative de découverte d'un pair par scan est une épreuve de Bernoulli avec deux issues : trouvé ou non trouvé.

La probabilité d'avoir $k$ succès est donnée par : 

$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
$$

Avec : 

- $n = 1{,}2096 \times 10^9$ nombre d'épreuves,

- $p = \frac{1}{4\,294\,967\,296} \approx 2,33 \times 10^{-8}$ probabilité de succès.

Selon le théorème de convergence de Poisson ( $n \to \infty \text{ et } p \to 0$ ) la loi binomiale $B(n,p)$ tend vers la loi de Poisson $P(\lambda)$ avec $\lambda = n p$, soit : 

$$
\lambda = n \times p = 1{,}2096 \times 10^9 \times 2,33 \times 10^{-8} \approx 0,2816
$$

La probabilité de trouver au moins un pair $X \ge 1$ sur la durée du bail est :

$$
P(X \ge 1) = 1 - e^{-\lambda} = 1 - e^{-0,282} \approx 0,245 \text{ (soit 24,5\%)}
$$

Un pair a 24,5% de chance de trouver un autre pair sur le réseau d'adressage IPv4 à bail $\approx$ 14 jours, et ce, dans le meilleur des mondes si ces conditions sont remplies : 

- Que le pair qui cherche un autre pair dédie 100% de son temps et sa bande passante à scanner pendant 14 jours le réseau à $v=10^3$ requêtes par seconde.

- Que l'adresse IP dur en effet 14 jours, ce qui n'est pas assuré dans un usage réel.

Une fois un pair découvert, une nouvelle difficulté se pose : comment vérifier qu’il appartient réellement au réseau ? Comment garantir l’authenticité de l’identité du pair découvert ? Ce sujet fera l’objet d’un prochain article.