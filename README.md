# El multiplicator

## La boucle pour générer le select


On commence par déclarer un ```<form>``` dans le html :
```
  <form action="index.php" method="post">
  // On écrit le code ici
  </form>
```

Dans ce form, on déclare un ```<select>``` en html, on déclare la page index.php dans le paramètre action, afin que le traitement se fasse sur la même page que le formulaire:

```
  <select class"" name="number_multiplication">

  </select>
```

Dans ce select, on va faire une boucle en php pour générer les valeurs de la table de multiplication:

```
<?php
for($i = 0; $i <=10; $i++){
  echo '<option value="'.$i.'"> Table' . $i . '</option>' ;
}
 ?>
```

On écrit une structure de boucle for classique avec une initialisation de la variable $i à 1, une condition d'arrêt de la boucle et un opérateur d'incrémentation.
Ensuite, on affiche les itérations de la boucle avec un echo. Toute la difficulté réside dans l'utilisation des simples quote et double quote pour concaténer du html et du php.

En effet, dans une balise php, le html s'écrit sous forme de chaine de  caractère. Par convention, nous allons utiliser les double quotes pour la syntaxe html, et les simples quote pour arrêter la chaine de caractère et recommencer à écrire du php.


Le résultat c'est un select avec dix options alors qu'on en déclare qu'une seule option, en économisant dix lignes, c'est ce qui s'appelle ***optimiser son code***.

##L'affichage d'une table

On ouvre la balise php à l'exterieur du formulaire, on commence par déclarer une varaible $multiplication qui va récupérer, la valeur contenue dans  la superglobale ```$_POST``` à laquelle on passe en paramètre le name du select du formulaire.

```
  $multiplication = $_POST['number_multiplication'];
```

On va multiplier cette valeur par les nombres de 1 à 10. Pour ce faire on fait une nouvelle boucle , aussi classique que la précédente :

```
for($i = 0; $i <=10; $i++){
  // On écrit le code ici
}
```

Dans la boucle, la variable $i contient un nombre de 1 à 10, on va multiplier ce nombre par la valeur récupérer dans la variable $multiplication et stocker ce résultat dans une variable $sum.
Il ne nous reste plus qu'a affficher le résultat avec un echo:

```
for($i = 1; $i<= 10; $i++){
  $sum = ($multiplication * $i);
  echo $multiplication . " X " . $i . " = " . $sum . "<br>";
}
```
**Last but not least**, on encadre la boucle par une condition; on passe en paramètre la fonction isset() à cette condition et on passe en paramètre de cette fonction la superglobale ```$_POST``` pour éviter d'avoir une erreur au premier chargement de index.php.

```
if(isset($_POST['number_multiplication'])){

  // On met la boucle ici

}

```
## Le code complet
```
<!DOCTYPE html>
<html lang="fr" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Multiplication</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
  </head>
  <body>

    <form action="index.php" method="post">
      <select class"" name="number_multiplication">

        <?php
        for($i = 0; $i <=10; $i++){
          echo '<option value="'.$i.'"> Table' . $i . '</option>' ;
        }
         ?>

       </select>
       <input type="submit" name="" value="envoyer">
     </form>


     <?php
    if(isset($_POST['number_multiplication'])){
      $multiplication = $_POST['number_multiplication'];

     for($i = 1; $i<= 10; $i++){
       $sum = ($multiplication * $i);
       echo $multiplication . " X " . $i . " = " . $sum . "<br>";
     }
   }
      ?>


  </body>
</html>
```
