# SMTP Injection Examples

L'injection SMTP consiste à insérer des retours à la ligne dans les champs d'une application envoyant des e-mails, pour ajouter des en-têtes ou corps non désirés.

```
To: victim@example.com
Subject: Contact form submission
From: attacker@example.com\r\nBcc: attacker2@example.com
```
```php
// Exemple vulnérable en PHP
mail($to, $subject, $message, "From: $email_address");
# Si $email_address = "attacker@x.com\r\nBcc: victim2@x.com", on injecte un Bcc.
```

> **Astuces** : Validez/réjectez tout CRLF dans les adresses, utilisez des APIs d'envoi sécurisées.
