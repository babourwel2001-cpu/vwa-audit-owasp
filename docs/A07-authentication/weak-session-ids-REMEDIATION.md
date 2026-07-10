# Weak Session IDs - Remédiation

**Module** : Weak Session IDs  
**Catégorie OWASP** : A07:2021 - Authentication Failures
**Date** : 10/07/2026 

---

## Mesures appliquées

**Blocage du module Weak Session IDs**
Le module a été désactivé au niveau Apache pour empêcher toute exposition des sessions vulnérables.

Fichier : `/var/www/html/DVWA/.htaccess`

```apache
<Location "/DVWA/vulnerabilities/weak_id/">
    Require all denied
</Location>
```
##Recommandation
-Utiliser le cookie de session PHP (PHPSESSID) plutôt qu'un cookie personnalisé
-Modifier le code du module pour utiliser des hashs à tous les niveaux
-Régénérer l'ID de session après chaque connexion
-Lier la session à l'adresse IP de l'utilisateur
