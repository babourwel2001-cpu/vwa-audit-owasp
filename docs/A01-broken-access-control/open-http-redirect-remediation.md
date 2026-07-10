# Open HTTP Redirect - Remédiation

**Module** : Open HTTP Redirect  
**Catégorie OWASP** : A01:2021 - Broken Access Control
**Date** : 10/07/2026 

---

### Mesures appliquées

**Filtrage des URLs externes**
Fichier : `/etc/apache2/conf-available/redirect.conf`

Blocage des requêtes contenant des URLs externes (`http://`, `https://`, `ftp://`, `www.`) dans le paramètre `id`.

```apache
<Location "/DVWA/vulnerabilities/open_redirect/source/">
    <IfModule mod_rewrite.c>
        RewriteEngine On
        RewriteCond %{QUERY_STRING} (http|https|ftp|www\.) [NC]
        RewriteRule .* - [F,L]
    </IfModule>
</Location>
```
---

### Test de validation

-- Requête testée : ?id=http://google.com

-- Résultat avant remédiation : Redirection vers google.com

-- Résultat après remédiation : 403 Forbidden

---

### Limites

-- Apache ne peut pas distinguer un clic légitime d'une modification manuelle

-- Une validation stricte des entrées côté code reste la solution la plus fiable

---

### Recommandations

-- Valider strictement le paramètre id côté serveur

-- Utiliser une liste blanche de valeurs autorisées

-- Ne pas exposer les paramètres de redirection dans l'URL

---
