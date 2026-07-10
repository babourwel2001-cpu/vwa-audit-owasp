# XSS Stored - Remédiation

**Module** : XSS Stored  
**Catégorie OWASP** : A03:2021 - Injection  
**Date** : 10/07/2026

---

### Mesures appliquées

**ModSecurity - Filtrage des requêtes POST**
Fichier : `/etc/modsecurity/conf.d/xss-stored.conf`

Blocage des patterns XSS dans les requêtes POST : `<script`, `javascript:`, `onerror`, `onload`, `onclick`, `alert`, `prompt`, `confirm`.

```apache
SecRule REQUEST_BODY "(<script|javascript:|onerror|onload|onclick|alert|prompt|confirm)" \
    "id:500001,phase:2,block,msg:'XSS detecte'"
```
---

### Activation de ModSecurity

-- Fichier : /etc/modsecurity/modsecurity.conf
-- SecRuleEngine On

---

---

### Test de validation

-- Requête testée : Message <script>alert('XSS')</script>

-- Résultat avant remédiation : Pop up d'alerte affichée

-- Résultat après remédiation : 403 Forbidden

---
---

### Limites

-- Les règles ModSecurity peuvent bloquer des requêtes légitimes

--  Une validation stricte des entrées côté code reste la solution la plus fiable

---
---

### Recommendations

-- Échapper systématiquement les sorties HTML avec htmlspecialchars()

--  Valider et filtrer toutes les entrées utilisateur

--   Utiliser une Content-Security-Policy stricte

---


