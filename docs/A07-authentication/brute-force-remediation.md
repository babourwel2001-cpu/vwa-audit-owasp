# Brute Force - Remédiation

**Module** : Brute Force  
**Catégorie OWASP** : A07:2021 - Authentication Failures
**date** : 09/07/2026 

---

## Mesures appliquées

**HTTPS**
Redirection forcée de HTTP vers HTTPS.

**Mot de passe admin**
Le mot de passe par défaut a été modifié en base de données.

**Restriction IP**
Accès au module brute force limité à une IP autorisée via .htaccess.

**Surveillance**
Un script surveille les logs Apache et alerte sur les tentatives multiples.

---

## Recommandations

- Mettre en place un CAPTCHA
- Ajouter une authentification multi-facteurs
- Verrouiller le compte après plusieurs échecs

---

## Conclusion

Les mesures configurées au niveau serveur renforcent la sécurité, mais un blocage automatique nécessiterait une modification du code applicatif.

**Date** : 09/07/2026
