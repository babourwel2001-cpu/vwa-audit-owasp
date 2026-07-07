# Weak Session IDs - Rapport d'audit

**Catégorie OWASP Top 10** : A07:2021 - Identification and Authentication Failures
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/weak_id/
**Date du test** : 07/07/2026

---

## Messages observés

L'ID de session est visible dans le cookie `dvwaSession` (outils développeur → Stockage → Cookies)

---

## Résultats des tests

### Niveau LOW

**Test : Observation des IDs**

- ID initial : 1
- Après rechargement : 2
- Après rechargement : 3
- Après rechargement : 4
- ...
- Après rechargement : 22
- Après rechargement : 23

**Observation** : Les IDs de session sont incrémentés de 1 à chaque rechargement. Ils sont donc parfaitement prévisibles.

---

### Niveau IMPOSSIBLE

**Test : Observation des IDs**

- ID affiché : 23
- Après rechargement : 23
- Après rechargement : 23
- Après rechargement : 23

**Observation** : L'ID de session reste fixe, même après plusieurs rechargements.

---
