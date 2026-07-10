# JavaScript Attacks - Remédiation

**Module** : JavaScript Attacks  
**Catégorie OWASP** : A07:2021 - Authentication Failures
**Date** : 10/07/2026 

---

### Mesures appliquées

**Tentative de blocage du fichier JavaScript source**
Fichier : `/etc/apache2/conf-available/javascript.conf`

```apache
<Location "/DVWA/vulnerabilities/javascript/source/low.js">
    Require all denied
</Location>
```
---

---

### Test de validation

-- Méthode : document.getElementById("token").value

-- Résultat : **Échec**  de la remédiation. La fonction generate_token() est toujours accessible, et le fichier JS peut être contourné.

---

---

### Limites

-- Le script est intégré dans la page HTML, le simple blocage du fichier JS ne suffit pas

--  Le code source reste accessible via la console et les outils développeur

---

### Recommandations

--  Ne jamais se fier à la validation côté client uniquement

--  Toujours valider les données côté serveur

-- Utiliser des tokens CSRF générés côté serveur

--Ne pas exposer la logique métier dans le JavaScript

-- Pour une sécurisation complète, il est nécessaire de modifier le code PHP pour ajouter une validation serveur
