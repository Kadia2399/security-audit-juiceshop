# Rapports d'Analyse de Sécurité

Ce dossier regroupe les artefacts et journaux de scans générés lors de l'exécution du pipeline de sécurité.

## 1. Fichiers Prévus
- `npm-audit-report.json` : Résultat de l'analyse SCA (vulnérabilités des dépendances).
- `pipeline.log` : Journal d'exécution des étapes de contrôle.

## 2. Synthèse d'Audit SCA (Exemple)
| Niveau de Sévérité | Nombre | Action Requise |
| :--- | :--- | :--- |
| **Critical** | 3 | Bloquer le déploiement |
| **High** | 7 | Correction obligatoire |
| **Moderate** | 12 | Mise à jour planifiée |
| **Low** | 5 | Toléré sous surveillance |
