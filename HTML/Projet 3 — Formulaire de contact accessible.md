---
title: Projet 3 — Formulaire de contact accessible

---

Etape 1 - Structurer le formulaire avec les bons éléments HTML

```html
<!DOCTYPE html>
<html lang="fr">
    <head>
        <title>Formulaire</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="formulaire2.css">
    </head>
    <body>
        <header>
            <h1>Formulaire</h1>
             <nav>
                <a href="contactformulaire.html">Contactez-nous</a>
             </nav>
        </header>
        <form action="traitement.php" method="post">
<section>
  <div>
    <label for="nom">Nom :</label>
    <br>
    <input type="text" id="nom" name="nom" required>
  </div>
  <div>
    <label for="prénom">Prénom :</label>
    <br>
    <input type="text" id="prénom" name="prénom" required>
  </div>
  <div>
    <label for="deuxième prénom">Deuxième Prénom (facultatif) : </label>
    <br>
    <input type="text" id="deuxième prénom" name="deuxième prénom" optional>
  </div>
  <div>
    <label for="âge">Age :</label>
    <br>
    <input type="text" id="âge" name="âge" required>
  </div>
  <div>
    <label for="adresse">Adresse :</label>
    <br>
    <input type="text" id="adresse" name="adresse" required>
  </div>

  <div>
    <label for="email">E-mail :</label>
    <br>
    <input type="email" id="email" name="email" required>
  </div>
  <div>
      <label for="message">Message <span aria-hidden="true">*</span></label>
      <br>
      <textarea 
        id="message" 
        name="message" 
        rows="5" 
        required 
        minlength="10"
      ></textarea>
    </div>
  <div>
    <button type="submit">Envoyer</button>
  </div>
  
</form>
</section>

    </body>
</html>
```

Etape 2 - Appliquer un style CSS accessible

```css
h1{
    text-align: center;
}
nav{
    text-align: right;
}
section{
    text-align: center;
}
```
Etape 3 - Tester la navigation au clavier uniquement
![image](https://hackmd.io/_uploads/ByPitzj6Mx.png)
