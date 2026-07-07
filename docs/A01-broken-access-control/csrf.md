# CSRF - Rapport d'audit

**Catégorie OWASP Top 10** : A01:2021 - Broken Access Control
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/csrf/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
Password Changed

---

## Résultats des tests

### Niveau LOW

**Test : Changement de mot de passe**
- Mot de passe actuel : Non demandé
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_new=test123&password_conf=test123&Change=Change&user_token=1f488dc8b5d09a69e48752d5bef5f971#


### Niveau MEDIUM

**Test : Changement de mot de passe**
- Mot de passe actuel : Non demandé
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_new=test123&password_conf=test123&Change=Change&user_token=1f488dc8b5d09a69e48752d5bef5f971#


### Niveau HIGH

**Test : Changement de mot de passe**
- Mot de passe actuel : Non demandé
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_new=test123&password_conf=test123&Change=Change&user_token=1f488dc8b5d09a69e48752d5bef5f971#


### Niveau IMPOSSIBLE

**Test : Changement de mot de passe**
- Mot de passe actuel : password123 (demandé)
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_current=password123&password_new=test123&password_conf=test123&Change=Change&user_token=a10b6a051486d849007af2c15a8ed726#

**Observation** : Le mot de passe actuel est demandé, ce qui rend l'attaque CSRF plus difficile.


## Recommandations

- Utiliser des tokens CSRF pour chaque requête
- Ne pas utiliser la méthode GET pour les actions sensibles
- Demander le mot de passe actuel pour les changements
- Valider le referer HTTP
- Utiliser POST au lieu de GET
# CSRF - Rapport d'audit

**Catégorie OWASP Top 10** : A01:2021 - Broken Access Control
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/csrf/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
Password Changed

**Échec** :
-(Message non affiché, la page se recharge)
-Passwords did not match or current password incorrect.

---

## Résultats des tests

### Niveau LOW

**Test : Changement de mot de passe**
- Ancien mot de passe : (non demandé)
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_new=test123&password_conf=test123&Change=Change&user_token=1f488dc8b5d09a69e48752d5bef5f971#

**Observation** : Le mot de passe actuel n'est pas demandé. Les paramètres sont visibles dans l'URL.

---

### Niveau MEDIUM

**Test : Changement de mot de passe**
- Ancien mot de passe : (non demandé)
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_new=test123&password_conf=test123&Change=Change&user_token=1f488dc8b5d09a69e48752d5bef5f971#

**Observation** : Le mot de passe actuel n'est pas demandé. Les paramètres sont visibles dans l'URL.

---

### Niveau HIGH

**Test : Changement de mot de passe**
- Ancien mot de passe : password123 (demandé)
- Nouveau mot de passe : test123
- Résultat : Password Changed

**URL observée** :
http://localhost/DVWA/vulnerabilities/csrf/?password_current=password123&password_new=test123&password_conf=test123&Change=Change&user_token=a10b6a051486d849007af2c15a8ed726#

**Observation** : Le mot de passe actuel est demandé. Les paramètres sont visibles dans l'URL.


iser POST au lieu de GET
