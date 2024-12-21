# Quiz App - Vue 3

Une application de quiz alimentée par un fichier `quizz.json`, construite avec Vue 3 et Bootstrap 5. Ce projet permet de réaliser un quiz de connaissances générales avec une interface simple et épurée.

---

## Fonctionnalités

- **Questions dynamiques** : Le quiz charge ses questions et réponses depuis un fichier `quizz.json`.
- **Progression** : Affiche une barre de progression pendant le quiz.
- **Réponses multiples** : Choisissez une réponse parmi les options et passez à la question suivante.
- **Message de succès ou d'échec** : À la fin du quiz, un message apparaît en fonction du score de l'utilisateur par rapport au score minimum.

---

## Structure du projet

- **App.vue** : Composant principal qui charge et gère l'ensemble du quiz.
- **QuizzApp.vue** : Gère la logique de déroulement du quiz (questions, réponses, score).
- **QuizzQuestion.vue** : Affiche chaque question et ses choix de réponse.
- **RadioButton.vue** : Composant pour afficher les boutons radio pour les réponses.
- **SimpleButton.vue** : Bouton pour passer à la question suivante.
- **ProgressBar.vue** : Affiche la progression du quiz en fonction des questions restantes.

---

## Exemple de fichier `quizz.json`

```json
{
  "title": "Quiz de connaissances générales",
  "minimum_score": 5,
  "success_message": "Félicitations ! Vous avez réussi le quiz.",
  "failure_message": "Dommage ! Vous n'avez pas atteint le score minimum.",
  "questions": [
    {
      "question": "Quelle est la capitale de la France ?",
      "choices": ["Paris", "Lyon", "Marseille", "Bordeaux"],
      "correct_answer": "Paris"
    },
    ...
  ]
}
```

---

## Installation

1. Clonez ce dépôt :

   ```bash
   git clone https://github.com/Amanda-Safoura/quizz-app-vue3.git
   ```

2. Accédez au répertoire du projet :

   ```bash
   cd quizz-app-vue3
   ```

3. Installez les dépendances :
   ```bash
   npm install
   ```

---

## Lancer l'application

Pour démarrer le serveur de développement :

```bash
npm run dev
```

Accédez à l'application dans votre navigateur à l'adresse suivante : [http://localhost:5173](http://localhost:5173).

---

## Licence

Ce projet est sous licence **MIT**.  
Consultez le fichier `LICENSE` pour plus de détails.
