# CRLF Injection Examples

Les injections CRLF exploitent l'insertion de caractères de fin de ligne (Carriage Return, Line Feed) pour altérer des entêtes HTTP, journaux, ou protocoles textuels.

```http
# Exemple d'injection dans une requête HTTP pour injecter un en-tête
GET / HTTP/1.1
Host: example.com
X-Injected: legit
X-Injected: attack
X-Evil: injected

# Résultat après interprétation:
GET / HTTP/1.1
Host: example.com
X-Injected: legit
X-Injected: attack
X-Evil: injected
```

```bash
# Injection dans une entrée de journal syslog via %0D%0A
echo "Normal log entry%0D%0AAttacker log entry" >> /var/log/app.log
```

> **Astuces** : URL-encodez `` (`%0D`) et `
` (`%0A`), testez sur différents parseurs.
