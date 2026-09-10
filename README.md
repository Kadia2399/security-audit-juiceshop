# Évaluation de Sécurité & Pipeline DevSecOps - Licence 3 Cybersécurité

Ce dépôt contient l'ensemble des livrables techniques pour l'évaluation de sécurité de l'application OWASP Juice Shop, l'analyse des risques (CIA), les propositions de remédiation, ainsi que l'automatisation des contrôles dans un pipeline CI/CD Jenkins.

## 1. Structure du Dépôt
- `Jenkinsfile` : Définition du pipeline déclaratif CI/CD intégrant les scans de sécurité.
- `screenshots/` : Preuves visuelles des vulnérabilités identifiées (V1 à V5).
- `remediation/` : Explications et correctifs de sécurité appliqués.
- `reports/` : Rapports générés par les contrôles automatisés.
- `security-config/` : Règles et configurations des scanners de sécurité.

## 2. Vulnérabilités Identifiées
- **V1 — Injection SQL (Bypass d'authentification) [CWE-89]** : Contournement du formulaire de connexion admin.
- **V2 — Cross-Site Scripting réfléchi (DOM-XSS) [CWE-79]** : Exécution de code via la barre de recherche.
- **V3 — Redirection Ouverte (Open Redirect) [CWE-601]** : Redirection non contrôlée via le paramètre d'URL.
- **V4 — Absence des drapeaux de sécurité sur les cookies [CWE-1275]** : Cookie de session sans `HttpOnly` ni `Secure`.
- **V5 — Exposition du jeton JWT côté client [CWE-200]** : Lecture du jeton de session via JavaScript (`document.cookie`).

## 3. Outils Utilisés
- **Cible de test** : OWASP Juice Shop
- **Automatisation CI/CD** : Jenkins
- **Analyse SCA (Dépendances)** : `npm audit`
- **Analyse SAST / Secrets** : `gitleaks` / `semgrep`

## 4. Instructions d'Exécution

### Lancement de l'application cible
```bash
git clone [https://github.com/juice-shop/juice-shop.git](https://github.com/juice-shop/juice-shop.git)
cd juice-shop
npm install
npm start
