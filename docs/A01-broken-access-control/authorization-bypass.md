# Authorization Bypass - Rapport d'audit

**Catégorie OWASP Top 10** : A01:2021 - Broken Access Control
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/authbypass/
**Date du test** : 08/07/2026

---

## Description de la faille

L'application ne vérifie pas côté serveur si l'utilisateur connecté possède les droits requis avant d'afficher la page. Un attaquant peut accéder directement à des pages normalement réservées aux administrateurs.

---

## Résultats des tests

### Niveau LOW

**Test : Accès direct à la page restreinte**

1. Se connecter avec un utilisateur non privilégié (ex: gordonb / abc123)
2. Modifier manuellement l'URL pour accéder à la page protégée
3. Exemple : passer de `login.php` à `/vulnerabilities/authbypass/`

**Résultat** : Accès à la page avec la liste des utilisateurs

**Conclusion** : L'application ne vérifie pas les droits d'accès côté serveur.

---

### Niveau IMPOSSIBLE

**Sécurisation** : Le code est entièrement corrigé. Le contrôle d'accès est géré de manière stricte côté serveur. Chaque requête vérifie de manière unique que l'utilisateur possède bien la permission d'exécuter l'action demandée.

**Résultat** : L'accès à la page restreinte est bloqué pour les utilisateurs non autorisés.

---
