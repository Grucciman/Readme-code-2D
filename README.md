# Readme-code-2D
Contient les informations qui décrivent le fonctionnement de la résolution numérique en 2D des équations de Molonari pour implémenter un terme de flux latéral

Le but du nouveau code est d'ajouter la contribution des flux d'eau latéraux à nos équations de température et de charge. L'équipe de 2024 avait pour cela rajouté un terme source volumique q dans l'équation 1D, ce qui ne fait pas de sens selon nous car le flux d'eau ne fait que transiter de droite à gauche (ou de gauche à droite) de l'aquifère, le bilan total net sur le capteur est donc nul si l'on isole une tranche dz pour réaliser le bilan (même quantité entrante et sortante).

Nous proposons donc une nouvelle approche, plus rigoureuse physiquement. Les équations seront traitées en 2D sur une grille très fine en terme de largeur autour de notre capteur, ce qui nous permettra de considérer qu'initialement, le profil est uniforme selon x.

$\usepackage{cancel}$

$H(z, \cancel{x}, t=0)$

$$
\frac{\partial \theta}{\partial t} = \kappa_e \Delta \theta + \alpha_e \nabla H \cdot \nabla \theta
$$

$$
S_s \frac{\partial H}{\partial t} = K \Delta H
$$


On résoud cette équation avec une méthode de Cranck Nicholson
