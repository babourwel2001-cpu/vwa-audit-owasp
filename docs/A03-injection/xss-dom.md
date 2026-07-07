# XSS DOM - Rapport d'audit

**Catégorie OWASP Top 10** : A03:2021 - Injection
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/xss_d/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
(Aucun)

**Échec** :
La page reste en anglais. Les paramètres `?default=` et `#` sont ignorés.

---

## Résultats des tests

### Niveau LOW

**Test 1 : Comportement normal (paramètre ignoré)**
- Payload : ?default=French
- Résultat : La page reste en anglais. Le paramètre est inactif.

**Test 2 : Tentative d'injection XSS via le paramètre default**
- Payload : ?default=<script>alert('XSS')</script>
- Résultat : Échec. Le paramètre est ignoré.

**Test 3 : Tentative d'injection XSS via le fragment (#)**
- Payload : #<script>alert('XSS')</script>
- Résultat : Échec. Rien ne se passe.

---

### Niveau IMPOSSIBLE

**Test 1 : Tentative d'injection XSS**
- Payload : ?default=<script>alert('XSS')</script>
- Résultat : Échec.

---

## Conclusion

Le module XSS DOM n'est pas fonctionnel sur cette installation de DVWA. Les paramètres sont ignorés, ce qui rend les tests impossibles.

---

