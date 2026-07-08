# Open HTTP Redirect - Rapport d'audit

**Catégorie OWASP Top 10** : A01:2021 - Broken Access Control
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/open_redirect/
**Date du test** : 08/07/2026

---

## Messages observés

**Succès** :
(Affichage de la citation)

**Échec** :
(Message d'erreur éventuel)

---

## Résultats des tests

### Niveau LOW

**Test 1 : Comportement normal**
- Payload : id=1
- Résultat : Affichage de la citation 1

**Test 2 : Comportement normal**
- Payload : id=2
- Résultat : Affichage de la citation 2

**Test 3 : ID inexistant**
- Payload : id=3
- Résultat : citaion = Some other stuff


**Test 4 : Injection de paramètre**
- Payload : id=1&redirect=http://google.com
- Résultat : Affichage de la citation 1

---

### Niveau IMPOSSIBLE

**Test 1 : Tentative de redirection externe**
- Payload : id=3
- Résultat : Meme resultat

**Test 2 : Injection de paramètre**
- Payload : id=1&redirect=http://google.com
- Résultat : Meme resultat

---
