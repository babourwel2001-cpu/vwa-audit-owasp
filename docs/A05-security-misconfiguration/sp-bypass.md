# CSP Bypass - Rapport d'audit

**Catégorie OWASP Top 10** : A05:2021 - Security Misconfiguration
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/csp/
**Date du test** : 07/07/2026

---

## Résultats des tests

### Niveau LOW

**Test : Bouton Include**

Le bouton "Include" tente de charger un script via `javascript:toggleTheme();` mais la CSP bloque cette exécution.

**Erreur observée** : Content-Security-Policy: The page's settings blocked an event handler (script-src-attr) from being executed because it violates the following directive: "script-src 'self' https://pastebin.com http://hastebin.com ..."

Source: javascript:toggleTheme();`

### Niveau IMPOSSIBLE

**Test : Check the sum**

**Code HTML observé** :
```html
<form name="csp" method="POST">
  <p>1+2+3+4+5= <span id="answer">15</span></p>
  <input id="solve" type="button" value="Solve the sum">
</form>
<script src="source/impossible.js"></script>
```


Résultat : La réponse 15 est affichée dans le HTML. Le script impossible.js gère la logique.
Faille identifiée : La validation est effectuée côté client (JavaScript). La réponse 15 est exposée dans le HTML et peut être facilement contournée.
