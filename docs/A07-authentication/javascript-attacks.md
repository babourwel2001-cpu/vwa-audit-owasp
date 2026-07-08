# JavaScript Attacks - Rapport d'audit

**Catégorie OWASP Top 10** : A07:2021 - Identification and Authentication Failures
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/javascript/
**Date du test** : 08/07/2026

---

## Description de la faille

La validation est effectuée uniquement côté client en JavaScript. Le token est généré dans le navigateur et peut être récupéré facilement via la console.

---

## Résultats des tests

### Niveau LOW

**Test : Récupération du token**
- Méthode : Ouvrir la console (F12) et taper `document.getElementById("token").value`
- Résultat : `d41d8cd98f00b204e9800998ecf8427e`

---

### Niveau IMPOSSIBLE

**Message affiché** :
"You can never trust anything that comes from the user or prevent them from messing with it and so there is no impossible level."

**Explication** : La validation côté client ne peut jamais être sécurisée, car l'utilisateur a toujours accès au code et peut le modifier.

---

