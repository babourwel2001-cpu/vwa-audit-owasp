# File Inclusion - Rapport d'audit

**Catégorie OWASP Top 10** : A01:2021 - Broken Access Control
**Sévérité** : Élevée
**URL testée** : http://localhost/DVWA/vulnerabilities/fi/
**Date du test** : 06/07/2026

---

## Messages observés

**Succès** :
Affichage du contenu du fichier

**Échec** :
Warning: include(): Failed opening ... No such file or directory

---

## Résultats des tests

### Niveau LOW

**Test 1 : Lecture de /etc/passwd**
- Payload : ?page=/etc/passwd
- Résultat : Contenu du fichier /etc/passwd affiché

**Test 2 : Traversée de répertoires**
- Payload : ?page=../../../etc/passwd
- Résultat : Échec (fichier non trouvé)

**Test 3 : Inclusion distante**
- Payload : ?page=http://google.com
- Résultat : Page Google affichée avec erreurs de headers

---

### Niveau MEDIUM

**Test 1 : Lecture sans traversée**
- Payload : ?page=etc/passwd
- Résultat : Échec (fichier non trouvé)

**Test 2 : Traversée de répertoires**
- Payload : ?page=../../../etc/passwd
- Résultat : Échec (fichier non trouvé)

**Test 3 : Tentative avec etc/passwd**
- Payload : ?page=etc/passwd
- Résultat : Échec (fichier non trouvé)

---

### Niveau HIGH

(A tester)

---

### Niveau IMPOSSIBLE

**Test 1 : Traversée de répertoires**
- Payload : ?page=../../../etc/passwd
- Résultat : ERROR: File not found!

**Test 2 : Contournement avec préfixe file**
- Payload : ?page=file/../../../etc/passwd
- Résultat : ERROR: File not found!

**Test 3 : Double encodage**
- Payload : ?page=..%252F..%252F..%252Fetc%252Fpasswd
- Résultat : ERROR: File not found!

---

## Recommandations

- Ne pas inclure de fichiers basés sur l'entrée utilisateur
- Utiliser une liste blanche de fichiers autorisés
- Désactiver allow_url_include dans php.ini
- Valider et filtrer strictement les entrées
