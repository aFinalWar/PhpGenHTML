# PhpGenHTML
A little PHP framework to easily generate clean HTML code, with automatic identation.  
Un petit framework PHP pour générer facilement du code HTML propre, avec une indentation automatique.

##Français

Vous pouvez regarder le fichier [sample.php](https://github.com/Drulac/PhpGenHTML/blob/master/sample.php), c'est un code exemple d'utilisation du framework.

### Chargement
Vous devez inclure le fichier [view.php](https://github.com/Drulac/PhpGenHTML/blob/master/view.php) qui contient le code du framework
```php
include('view.php');
```
Vous pouvez utiliser un alias pour gagner du temps en écrivant moins de caractères à chaques fois
```php
use PhpGenHTML as V;
```
Créez une variable contenant un objet View, du namespace PhpGenHTML (ici l'alias `V` est utilisé). Cette variable qui va nous servir pour récuper le code HTML à afficher.
```php
$view = New V\View();
```
Affichez ensuite le retour de la fonction `start()` pour afficher le doctype HTML et le tag HTML de départ.
```php
echo $view->start();
```

#### Récapitulatif :
```php
include('view.php');
use PhpGenHTML as V;
$view = New V\View();
echo $view->start();
```

### Balises

En HTML il y a 2 types de balises :
 - Les balises orphelines (exemple `<img>`)
 - Les balises en paires (exemple `<div></div>`)

Les balises orphelines possèdent différents attributs, tandis que les balises en paires peuvent accueillir du contenu, en plus des attributs.

Pour créer une balise, on utilise mot clé `new`, le namespace (ici l'alias `V` est utilisé), puis le nom de la balise
```php
new V\Div()
```
Pour les balises en paires, on donne comme arguments un tableau avec les balises enfants, puis un tableau associatif avec les attributs
```php
new V\Div(array(
  new V\Div()
), array('class' => 'test'))
```
On peut également passer directemnt un texte à la place du tableau de composant
```php
new V\Div('Contenu', array('class' => 'test'))
```
Les balises orphelines ne pouvant pas avoir de contenu, elles ne prennent qu'un tableau associatif pour les attributs comme argument.
```php
new V\Img(array('src' => 'images/img.png'))
```

Pour afficher des balises on utilise la fonction `view()` de notre variable `$view`
```php
$view->view();
```
cette fonction nous retourne le code HTML à afficher. Il faut donc faire un `echo`
```php
echo $view->view();
```
On donne à la fonction `view()` un tableau contenant les balises à afficher
```php
echo $view->view(array(
  new V\Div(array(
    new V\Div('Contenu', array('id' => 'subdiv'))
  ), array('class' => 'test')),
  new V\Img(array('src' => 'images/img.png'))
));
```
Le framework gérant l'indentation de l'HTML, vous n'avez pas à vous en soucier :smiley:











## English
###### Loading
You must include the code file.
```php
include('view.php');
```
You can use an alias to code faster, with less chars.
```php
use PhpGenHTML as PGH;
```
Make into a variable PGH object.
```php
$view = New PGH\View();
```
Print the return of the **start()** function to print the html doctype and the html start tag.
```php
echo $view->start();
```

### Sample :
```php
include('view.php');
use PhpGenHTML as PGH;
$view = New PGH\View();
echo $view->start();
```
