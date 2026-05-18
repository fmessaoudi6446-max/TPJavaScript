```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Exercice JS</title>
</head>
<body>

    <p id="texte">Texte original</p>

    <button onclick="changerTexte()">
        Changer le texte
    </button>

    <script>

        function changerTexte() {

            // Sélectionner le paragraphe
            const paragraphe = document.querySelector("#texte");

            // Changer le texte
            paragraphe.innerText = "Le texte a été changé !";
        }

    </script>

</body>
</html>
```
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Changer Couleur</title>
</head>
<body>

    <h1 id="titre">Je suis un titre</h1>

    <button onclick="changerCouleur('red')">
        Rouge
    </button>

    <button onclick="changerCouleur('green')">
        Vert
    </button>

    <button onclick="changerCouleur('blue')">
        Bleu
    </button>

    <script>

        function changerCouleur(couleur) {

            // Sélectionner le titre
            const titre = document.querySelector("#titre");

            // Changer la couleur
            titre.style.color = couleur;
        }

    </script>

</body>
</html>
```
# Exercice 3 : Ajouter du HTML

## Objectif
Ajouter du contenu HTML dans un div.

## Méthodes utilisées
- querySelector
- innerHTML

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Ajouter HTML</title>
</head>
<body>

    <div id="contenu"></div>

    <button onclick="ajouterHTML()">
        Ajouter du contenu
    </button>

    <button onclick="effacerHTML()">
        Effacer
    </button>

    <script>

        function ajouterHTML() {

            const div = document.querySelector("#contenu");

            div.innerHTML = `
                <h2>Nouveau contenu</h2>
                <p>Paragraphe ajouté avec innerHTML</p>
            `;
        }

        function effacerHTML() {

            const div = document.querySelector("#contenu");

            div.innerHTML = "";
        }

    </script>

</body>
</html>
```

---

# Exercice 4 : Ajouter et enlever des classes

## Objectif
Manipuler les classes CSS d'un élément.

## Méthodes utilisées
- querySelector
- classList.add()
- classList.remove()

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">

    <style>

        .style-special {
            color: white;
            background-color: blue;
            padding: 10px;
            font-size: 20px;
        }

    </style>

    <title>Classes CSS</title>
</head>
<body>

    <p id="para">
        Je suis un paragraphe normal
    </p>

    <button onclick="ajouterStyle()">
        Ajouter style
    </button>

    <button onclick="enleverStyle()">
        Enlever style
    </button>

    <button onclick="basculerStyle()">
        Basculer style
    </button>

    <script>

        const paragraphe = document.querySelector("#para");

        function ajouterStyle() {
            paragraphe.classList.add("style-special");
        }

        function enleverStyle() {
            paragraphe.classList.remove("style-special");
        }

        function basculerStyle() {
            paragraphe.classList.toggle("style-special");
        }

    </script>

</body>
</html>
```

---

# Exercice 5 : Modifier plusieurs éléments

## Objectif
Sélectionner et modifier tous les éléments d'une classe.

## Méthodes utilisées
- querySelectorAll
- boucle for

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Modifier plusieurs éléments</title>
</head>
<body>

    <p class="item">Item 1</p>
    <p class="item">Item 2</p>
    <p class="item">Item 3</p>
    <p class="item">Item 4</p>

    <button onclick="colorier()">
        Colorier tous
    </button>

    <button onclick="numeroter()">
        Numéroter
    </button>

    <script>

        function colorier() {

            const items = document.querySelectorAll(".item");

            for (let i = 0; i < items.length; i++) {

                items[i].style.color = "red";
            }
        }

        function numeroter() {

            const items = document.querySelectorAll(".item");

            for (let i = 0; i < items.length; i++) {

                items[i].innerText = "Élément numéro " + (i + 1);
            }
        }

    </script>

</body>
</html>
```
# Exercice 6 - Sélecteur de couleur 🎨

## Objectif
Créer un sélecteur de couleur qui change le background de la page avec JavaScript.

---

## Structure HTML

```html
<div class="container">
    <h1>🎨 Sélecteur de couleur</h1>
    <p class="subtitle">
        Cliquez sur une couleur pour changer le fond de la page
    </p>

    <div class="color-picker">
        <div class="color-box" style="background-color: #FF6B6B;" data-color="#FF6B6B"></div>
        <div class="color-box" style="background-color: #4ECDC4;" data-color="#4ECDC4"></div>
        <div class="color-box" style="background-color: #45B7D1;" data-color="#45B7D1"></div>
        <div class="color-box" style="background-color: #96CEB4;" data-color="#96CEB4"></div>
        <div class="color-box" style="background-color: #FFEAA7;" data-color="#FFEAA7"></div>
        <div class="color-box" style="background-color: #DDA0DD;" data-color="#DDA0DD"></div>
        <div class="color-box" style="background-color: #98D8C8;" data-color="#98D8C8"></div>
        <div class="color-box" style="background-color: #F7B787;" data-color="#F7B787"></div>
    </div>

    <button id="resetBtn">🔄 Réinitialiser</button>

    <div id="colorInfo">
        Couleur actuelle : 🌈
    </div>
</div>
```

---

## JavaScript

```javascript
// Sélection des éléments
const colorBoxes = document.querySelectorAll('.color-box');
const resetButton = document.querySelector('#resetBtn');
const colorInfo = document.querySelector('#colorInfo');

const defaultColor = '#f0f0f0';

// Fonction pour changer la couleur
function changeBackgroundColor(color, colorName) {
    document.body.style.backgroundColor = color;

    if (colorName) {
        colorInfo.textContent = `Couleur actuelle : ${colorName}`;
    } else {
        colorInfo.textContent = `Couleur actuelle : ${color}`;
    }
}

// Ajouter événement sur chaque couleur
colorBoxes.forEach(box => {
    box.addEventListener('click', function () {
        const color = this.style.backgroundColor;
        changeBackgroundColor(color, 'Couleur sélectionnée');
    });
});

// Reset
resetButton.addEventListener('click', function () {
    document.body.style.backgroundColor = defaultColor;
    colorInfo.textContent = 'Couleur actuelle : 🌈 (défaut)';
});
```

---

## Méthodes utilisées

- `querySelector()` → sélectionner un élément
- `querySelectorAll()` → sélectionner plusieurs éléments
- `style` → changer le CSS en JavaScript
- `classList` → gérer les classes CSS
- `addEventListener()` → gérer les clics

---

## Résultat attendu

- Cliquer sur une couleur change le fond de la page
- Le texte affiche la couleur actuelle
- Le bouton reset remet la couleur par défaut
# Exercice 7 : Formulaire dynamique

## Objectif
Afficher les valeurs du formulaire en temps réel.

## Méthodes
- querySelector
- value
- innerText

## HTML + JS

```html
<input type="text" id="nom" placeholder="Votre nom">

<input type="color" id="couleur">

<p id="affichage">
    Votre nom apparaîtra ici
</p>

<script>
const inputNom = document.querySelector("#nom");
const inputCouleur = document.querySelector("#couleur");
const affichage = document.querySelector("#affichage");

// Mise à jour en temps réel
inputNom.addEventListener("input", function () {
    affichage.innerText = inputNom.value;
});

inputCouleur.addEventListener("input", function () {
    affichage.style.color = inputCouleur.value;
});
</script>
```

---

# Exercice 8 : Liste TODO

## Objectif
Créer une liste de tâches.

## Méthodes
- querySelector
- innerHTML
- value

## Code

```html
<input type="text" id="tache" placeholder="Nouvelle tâche">

<button onclick="ajouter()">Ajouter</button>
<button onclick="vider()">Tout effacer</button>

<ul id="liste"></ul>

<script>

function ajouter() {
    const input = document.querySelector("#tache");
    const liste = document.querySelector("#liste");

    if (input.value !== "") {
        liste.innerHTML += "<li>" + input.value + "</li>";
        input.value = "";
    }
}

function vider() {
    document.querySelector("#liste").innerHTML = "";
}

</script>
```

---

# Exercice 9 : Compteur avec conditions

## Objectif
Changer le style selon la valeur.

## Méthodes
- querySelector
- innerText
- classList
- conditions

## Code

```html
<h1 id="compteur">0</h1>

<button onclick="plus()">+1</button>
<button onclick="moins()">-1</button>
<button onclick="reset()">Reset</button>

<script>

let compteur = 0;
const affichage = document.querySelector("#compteur");

function updateStyle() {
    affichage.classList.remove("negatif", "positif", "zero");

    if (compteur > 0) {
        affichage.classList.add("positif");
    } else if (compteur < 0) {
        affichage.classList.add("negatif");
    } else {
        affichage.classList.add("zero");
    }

    affichage.innerText = compteur;
}

function plus() {
    compteur++;
    updateStyle();
}

function moins() {
    compteur--;
    updateStyle();
}

function reset() {
    compteur = 0;
    updateStyle();
}
</script>

<style>
.positif { color: green; }
.negatif { color: red; }
.zero { color: black; }
</style>
```

---

# Exercice 10 : Afficher / Masquer des onglets

## Objectif
Créer des onglets interactifs.

## Méthodes
- querySelector
- querySelectorAll
- classList

## Code

```html
<div class="tabs">
    <button onclick="showTab(1)">Onglet 1</button>
    <button onclick="showTab(2)">Onglet 2</button>
    <button onclick="showTab(3)">Onglet 3</button>
</div>

<div class="content" id="tab1">Contenu de l'onglet 1</div>
<div class="content" id="tab2" style="display:none;">Contenu de l'onglet 2</div>
<div class="content" id="tab3" style="display:none;">Contenu de l'onglet 3</div>

<script>

function showTab(tab) {

    const tabs = document.querySelectorAll(".content");

    tabs.forEach(t => {
        t.style.display = "none";
    });

    document.querySelector("#tab" + tab).style.display = "block";
}

</script>
```