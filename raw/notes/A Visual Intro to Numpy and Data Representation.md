tags:: #thelaboratory/coding 
source:: [1](https://jalammar.github.io/visual-numpy/)

The [NumPy](https://www.numpy.org/) package is the workhorse of data analysis, machine learning, and scientific computing in the python ecosystem. It vastly simplifies manipulating and crunching vectors and matrices. Some of python’s leading package rely on NumPy as a fundamental piece of their infrastructure (examples include scikit-learn, SciPy, pandas, and tensorflow). Beyond the ability to slice and dice numeric data, mastering numpy will give you an edge when dealing and debugging with advanced usecases in these libraries.


### Créer des Arrays.

- Pour créer un numpy array (ndarray) en lui passant une liste python  et en utilisant np.array()
![[Pasted image 20240114180749.png]]

Il est possible d'utiliser des fonctions numpy pour générer automatiquement des arrays.

![[Pasted image 20240114180854.png]]


### Arithmétiques des Arrays.
- On peut additionner des listes
![[Pasted image 20240114180946.png]]

- Soustraire, multiplier, diviser...
![[Pasted image 20240114181007.png]]


### Indexage des arrays.
C'est comme en python.
![[Pasted image 20240114181049.png]]


### Aggregation.
![[Pasted image 20240114181103.png]]
- Il existe aussi mean, prod (produit de multiplication de tout les éléments entre eux), std (standard deviation)


### Création de matrices.

```python
np.array([[1,2],[3,4]])
```
![[Pasted image 20240114181215.png]]

Idem on peut appeler ones, zeros, ..
![[Pasted image 20240114181236.png]]

Les arithémtiques vu juste avant fonctionne aussi. Il est possible de faire des calculs sur des matrices de différentes tailles seulement si la matrice a une seule dimension (une seule ligne, ou colonne).
![[Pasted image 20240114181318.png]]

Sauf pour la multiplication :
![[Pasted image 20240114181636.png]]

### Indexage des matrices.

![[Pasted image 20240114181816.png]]


### Aggregation
![[Pasted image 20240114181911.png]]
![[Pasted image 20240114181857.png]]


### Transposing and Reshaping

La fonction reshape() de NumPy permet de changer la dimension de la matrice que l'on manipule.

![[Pasted image 20240114190631.png]]


### More Dimension.
NumPy peut réaliser tout ce que l'on vient de mentionner avant dans n'importe quelle dimension. 
![[Pasted image 20240114190734.png]]
![[Pasted image 20240114190803.png]]

Note : 
Keep in mind that when you print a 3-dimensional NumPy array, the text output visualizes the array differently than shown here. NumPy’s order for printing n-dimensional arrays is that the last axis is looped over the fastest, while the first is the slowest. Which means that `np.ones((4,3,2))` would be printed as:

```python
array([[[1., 1.],
        [1., 1.],
        [1., 1.]],

       [[1., 1.],
        [1., 1.],
        [1., 1.]],

       [[1., 1.],
        [1., 1.],
        [1., 1.]],

       [[1., 1.],
        [1., 1.],
        [1., 1.]]])
```



### Practical usage
Quelques exemples de l'utilité de NumPy.

#### Formules
Implémenter des formules mathématiques qui fonctionnent sur des matrices  et vecteurs est central dans la popularité de  NumPy. C'est pourquoi NumPy est maître dans le codage python de la recherche scientifique.

Considérons par exemple le Mean Square Error, important en machine learning.
![[Pasted image 20240114191230.png]]

implémenter cela est très facile avec NumPy :
![[Pasted image 20240114191249.png]]

