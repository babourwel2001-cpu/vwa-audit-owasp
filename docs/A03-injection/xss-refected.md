# XSS Reflected - Rapport d'audit

**Catégorie OWASP Top 10** : A03:2021 - Injection
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/xss_r/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
Hello [nom]

**Échec** :
(Aucun message d'erreur spécifique)

---

## Résultats des tests

### Niveau LOW

**Test 1 : Comportement normal**
- Payload : test
- Résultat : Hello test

**Test 2 : Injection XSS simple**
- Payload : <script>alert('XSS')</script>
- Résultat : Hello + vide + pop up d'alerte

**Test 3 : XSS avec image**
- Payload : <img src=x onerror=alert('XSS')>
- Résultat : Hello + icone image + pop up d'alerte

---

### Niveau IMPOSSIBLE

**Test 1 : Injection XSS simple**
- Payload : <script>alert('XSS')</script>
- Résultat : Hello <script>alert('XSS')</script>

**Test 2 : XSS avec image**
- Payload : <img src=x onerror=alert('XSS')>
- Résultat : Hello <img src=x onerror=alert('XSS')>

---

