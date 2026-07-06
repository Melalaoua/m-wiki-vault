tags:: #thelaboratory/AI 
source::[1](https://jalammar.github.io/illustrated-stable-diffusion/)

Stable diffusion est la capacité de générer des images à partir de descriptions textuelles. Les modèles sont de plus en plus performants dans ce domaine, jusqu'à dépasser l'Homme. Ceci souligne de sérieuses questions éthiques et morales, que je n'aborderais pas là.

Les modèles de stable diffusion sont constitués d'un module de compréhension de texte (encoder) et d'un générateur d'image.
![[Pasted image 20230628084333.png]]

L'encodeur prend en input un texte (la description) et en sort une liste de vecteur. L'information est ensuite transmise au générateur d'image.

