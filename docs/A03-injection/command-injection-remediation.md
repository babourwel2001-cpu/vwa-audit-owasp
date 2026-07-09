# Command Injection - Remédiation

**Module** : Command Injection  
**Catégorie OWASP** : A03:2021 - Injection  
**Date** : 09/07/2026

---

## Mesures appliquées

**Désactivation des fonctions système PHP**
Les fonctions `exec()`, `shell_exec()`, `system()`, `passthru()` et `pcntl_exec()` ont été désactivées dans le fichier `php.ini`.

---

## Test de validation

Requête testée : `127.0.0.1; whoami`

Résultat : `Fatal error: Call to undefined function shell_exec()`

---

## Niveau IMPOSSIBLE

Le niveau IMPOSSIBLE est déjà sécurisé. Il valide que l'entrée est une adresse IP valide.

Test : `127.0.0.1; whoami`  
Résultat : `ERROR: You have entered an invalid IP.`

---

## Limites

- L'application reste vulnérable si d'autres fonctions comme `eval()` ou `include()` sont utilisées
- La désactivation PHP n'empêche pas d'autres types d'injections
- Ces fonctions peuvent être nécessaires au bon fonctionnement d'autres applications

---

## Recommandations

- Valider strictement le format de l'entrée (IP uniquement)
- Utiliser une liste blanche de caractères autorisés
- Exécuter les commandes avec les droits les plus faibles possibles

---

**Date** : 09/07/2026
