# File Inclusion - Remédiation

**Module** : File Inclusion  
**Catégorie OWASP** : A01:2021 - Broken Access Control  
**Date** : 09/07/2026

---

## Mesures appliquées

**Désactivation de allow_url_include**
L'option `allow_url_include` a été désactivée dans le fichier `php.ini` dont le chemin est `/etc/php/8.4/apache2/php.ini  `pour empêcher l'inclusion de fichiers distants.

**Filtrage des caractères dangereux**
Les traversées de répertoires (`../`, `..\`), les inclusions distantes (`http://`, `https://`, `ftp://`) et les null bytes (`%00`) sont bloquées au niveau Apache.
Fichier : `/etc/apache2/conf-available/file-inclusion.conf`

**Restriction IP**
Accès au module File Inclusion limité à une IP autorisée via `.htaccess`.

---

## Test de validation

Requête testée : `http://localhost/DVWA/vulnerabilities/fi/?page=/etc/passwd`

Résultat avant remédiation : Affichage du fichier `/etc/passwd`

Résultat après remédiation : `403 Forbidden`

---

## Niveau IMPOSSIBLE

Le niveau IMPOSSIBLE est déjà sécurisé. Il utilise une liste blanche de fichiers autorisés.

Test : `http://localhost/DVWA/vulnerabilities/fi/?page=/etc/passwd`  
Résultat : `ERROR: File not found!`

---

## Limites

- Les règles Apache ne protègent que ce module spécifique
- D'autres paramètres ou modules pourraient rester vulnérables
- Une validation stricte des entrées côté code reste la solution la plus fiable

---

## Recommandations

- Utiliser une liste blanche de fichiers autorisés
- Valider strictement le paramètre `page`
- Désactiver `allow_url_include` sur tout le serveur
- Stocker les fichiers inclus hors de la racine web

---

**Date** : 09/07/2026
