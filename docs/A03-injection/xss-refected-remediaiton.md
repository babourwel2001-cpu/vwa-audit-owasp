# XSS Reflected - Remédiation

**Module** : XSS Reflected  
**Catégorie OWASP** : A03:2021 - Injection  
**Date** : 10/07/2026

---

### Mesures appliquées

**Content-Security-Policy (CSP) et Filtrage des caractères dangereux**
Fichier : `/etc/apache2/conf-available/xss.conf`

Ajout d'un en-tête CSP pour bloquer l'exécution de scripts inline et filtrage des caractères et mots-clés utilisés dans les attaques XSS : `<`, `>`, `javascript:`, `onerror`, `onload`, `onclick`.

```apache
Header always set Content-Security-Policy "default-src 'self'; script-src 'self';"

RewriteCond %{QUERY_STRING} (<|>|javascript:|onerror|onload|onclick) [NC]
RewriteRule .* - [F,L]
```
---

---
### Test de Validation

--Requête testée : <script>alert('XSS')</script>

--Résultat avant remédiation : Pop up d'alerte affichée

--Résultat après remédiation : 403 Forbidden

---
---
### Limites
  -- Les règles Apache ne protègent que ce module spécifique

  -- Une validation stricte des entrées côté code reste la solution la plus fiable


---
  
### Recommendations

  -- Échapper systématiquement les sorties HTML avec htmlspecialchars()

  -- Utiliser une Content-Security-Policy stricte

  -- Valider et filtrer toutes les entrées utilisateur

