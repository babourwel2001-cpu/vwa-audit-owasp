# Cryptography - Rapport d'audit

**Catégorie OWASP Top 10** : A02:2021 - Cryptographic Failures
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/cryptography/
**Date du test** : 08/07/2026

---

## Description de la faille

L'application utilise un algorithme de cryptage faible avec une clé exposée dans le code JavaScript. Un attaquant peut décrypter n'importe quel message.

---

## Résultats des tests

### Niveau LOW

**Test 1 : Encodage d'un message**
- Message : Hello
- Résultat : PwQPBBs=

**Test 2 : Décodage du message crypté**
- Chaîne : Lg4WGlQZChhSFBYSEB8bBQtPGxdNQSwEHREOAQY=
- Résultat : Your new password is: Olifant
- Mot de passe trouvé : Olifant

---

### Niveau IMPOSSIBLE

**Sécurisation** : Le code est corrigé. Le cryptage utilise un algorithme moderne (AES) avec une clé stockée côté serveur.

---
