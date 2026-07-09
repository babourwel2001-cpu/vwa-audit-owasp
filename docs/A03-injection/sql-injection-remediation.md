# SQL Injection - Remédiation

**Module** : SQL Injection  
**Catégorie OWASP** : A03:2021 - Injection  
**Date** : 09/07/2026

---

## Mesures appliquées

**Filtrage des mots-clés SQL au niveau Apache**
Fichier : `/etc/apache2/conf-available/sqli.conf`

Blocage des mots-clés SQL suivants : `SELECT`, `UNION`, `INSERT`, `DELETE`, `DROP`, `UPDATE`, `FROM`, `WHERE`, `OR`, `--`.

**Restriction IP**
Accès au module SQL Injection limité à une IP autorisée via `.htaccess`.

---

## Test de validation

Requête testée : `1' AND '1'='1`

Résultat avant remédiation : Affichage de tous les utilisateurs

Résultat après remédiation : `403 Forbidden`

---

## Niveau IMPOSSIBLE

Le niveau IMPOSSIBLE est déjà sécurisé. Il utilise des requêtes paramétrées.

---

## Limites

- Les règles Apache ne protègent que ce module spécifique
- Une validation stricte des entrées côté code reste la solution la plus fiable

---

## Recommandations

- Utiliser des requêtes paramétrées côté code
- Valider strictement le type de l'entrée (ex: numérique)
- Limiter les privilèges de la base de données

---

**Date** : 09/07/2026
