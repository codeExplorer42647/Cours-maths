# Cours-maths Password Protection

Ce projet montre comment protéger un fichier HTML statique (`protected.html`) à l'aide d'un mot de passe côté client. Les mots de passe restent visibles dans le JavaScript : la sécurité est donc limitée.

## Fichiers principaux
- `index.html` : page de connexion demandant le mot de passe.
- `protected.html` : document protégé affiché après validation.
- `assets/p1984.js` : mapping lisible **mot de passe → URL**.
- `assets/p1984.min.js` : version minifiée chargée par `index.html`.

## Scripts npm
- `npm install` : installe les dépendances (dont `terser`).
- `npm run minify` : génère `assets/p1984.min.js`.
- `npm run watch` : surveille `assets/p1984.js` et exécute `npm run minify` à chaque modification.

## Ajouter ou supprimer un mot de passe
1. Éditer `assets/p1984.js` :
```javascript
const passwordMapping = {
  "abc123": "protected.html"
};
```
2. Exécuter `npm run minify` pour mettre à jour `assets/p1984.min.js`.

## Intégration continue
Le workflow `.github/workflows/minify.yml` installe les dépendances via `npm install`, puis lance `npm run minify` à chaque push sur `main`. Si le fichier minifié change, il est automatiquement committé.
