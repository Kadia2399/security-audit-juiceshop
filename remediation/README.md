# Mesures de Remédiation et Sécurisation

Ce dossier présente les corrections techniques préconisées pour les vulnérabilités identifiées.

## 1. V1 — Injection SQL (CWE-89)
- **Cause** : Concaténation directe des entrées utilisateur dans la requête de base de données.
- **Remédiation** : Utiliser des requêtes paramétrées (Prepared Statements) ou les méthodes de l'ORM Sequelize.
- **Vérification** : La saisie de `' OR 1=1--` dans le formulaire renvoie une erreur 401 Unauthorized sans accès au compte.

## 2. V2 — Cross-Site Scripting réfléchi / DOM-XSS (CWE-79)
- **Cause** : Rendu dynamique de l'entrée utilisateur dans le DOM sans échappement contextuel.
- **Remédiation** : Encoder systématiquement les sorties HTML et utiliser l'interpolation native sécurisée du framework.
- **Vérification** : L'injection de code HTML/JS est rendue sous forme de texte inoffensif sans exécuter de script.

## 3. V4 & V5 — Sécurisation des cookies et exposition de session (CWE-1275, CWE-200)
- **Cause** : Le cookie contenant le jeton d'authentification n'a pas les attributs de protection.
- **Remédiation** : Définir les attributs `HttpOnly` (bloque la lecture via JavaScript) et `Secure` (force la transmission chiffrée HTTPS) lors de la création du cookie.
- **Vérification** : La commande `document.cookie` dans la console ne permet plus de lire le jeton JWT.
