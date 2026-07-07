
# Insecure CAPTCHA - Rapport d'audit

**Catégorie OWASP Top 10** : A07:2021 - Identification and Authentication Failures
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/captcha/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
Password Changed

**Échec** :
(Non applicable)

---

## Résultats des tests

### Niveau LOW

**Test : Changement de mot de passe**
- Mot de passe actuel : Non demandé
- Nouveau mot de passe : test123
- CAPTCHA : Non fonctionnel (clé API manquante)
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/captcha/?password_new=test123&password_conf=test123&Change=Change&step=1

**Observation** : Le CAPTCHA ne fonctionne pas car la clé API n'est pas configurée.

---

### Niveau IMPOSSIBLE

**Test : Changement de mot de passe**
- Mot de passe actuel : Non demandé
- Nouveau mot de passe : test123
- CAPTCHA : Non fonctionnel
- Résultat : Password Changed

**Observation** : Le CAPTCHA ne fonctionne pas car la clé API n'est pas configurée.

---


