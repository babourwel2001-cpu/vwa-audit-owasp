# Brute Force - Rapport d'audit

**Catégorie OWASP Top 10** : A07:2021 - Identification and Authentication Failures
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/brute/
**Date du test** : 06/07/2026

---

## Messages observés

**Succès** :
Welcome to the password protected area admin

**Échec** :
Username and/or password incorrect.

---

## Résultats des tests

### Niveau LOW

**Test 1 : Identifiants valides**
- Username : admin
- Password : password
- Résultat : Welcome to the password protected area admin

**Test 2 : Identifiants invalides**
- Username : admin
- Password : wrong
- Résultat : Username and/or password incorrect.

**Test 3 : Contournement SQL**
- Username : admin' OR '1'='1
- Password : (vide)
- Résultat : Welcome to the password protected area admin

---

### Niveau MEDIUM

**Test 1 : Identifiants valides**
- Username : admin
- Password : password
- Résultat : Welcome to the password protected area admin

**Test 2 : Identifiants invalides**
- Username : admin
- Password : wrong
- Résultat : Username and/or password incorrect.

**Test 3 : Contournement SQL**
- Username : admin' OR '1'='1
- Password : (vide)
- Résultat : Échec (le caractère ' est échappé par mysqli_real_escape_string)

---

### Niveau HIGH

**Test 1 : Identifiants valides**
- Username : admin
- Password : password
- Résultat : Welcome to the password protected area admin

**Test 2 : Identifiants invalides**
- Username : admin
- Password : wrong
- Résultat : Username and/or password incorrect.

---

## Recommandations

- Limiter le nombre de tentatives de connexion
- Ajouter un CAPTCHA après plusieurs échecs
- Utiliser des requêtes paramétrées
