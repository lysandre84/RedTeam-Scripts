# XPath Injection Examples

Les injections XPath permettent de manipuler des expressions XPath pour contourner une authentification XML.

```xml
<!-- Requête XPath vulnérable -->
/users/user[username/text()='{user}' and password/text()='{pass}']

<!-- Si user = admin' or '1'='1, pass = anything -->
/users/user[username/text()='admin' or '1'='1' and password/text()='anything']
```

```php
// PHP example
$xpath = "/users/user[username/text()='{$u}' and password/text()='{$p}']";
```

> **Prévention** : Validez et échappez les entrées, utilisez des parsers XML avec binding sécurisés.
