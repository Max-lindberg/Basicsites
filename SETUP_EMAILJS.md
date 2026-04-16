# EmailJS Setup Guide

For at få email-formularen til at virke, skal du opsætte EmailJS:

## 1. Opret EmailJS konto
1. Gå til https://www.emailjs.com/
2. Klik "Sign Up Free" (gratis op til 200 emails/måned)
3. Bekræft din email

## 2. Tilføj Email Service
1. I EmailJS dashboard, gå til "Email Services"
2. Klik "Add New Service"
3. Vælg din email udbyder (Gmail anbefales)
4. Følg instruktionerne for at forbinde din email
5. Kopier dit **Service ID** (fx: "service_abc123")

## 3. Opret Email Template
1. Gå til "Email Templates"
2. Klik "Create New Template"
3. Konfigurer template:

**To Email:** (i feltet)
```
{{to_email}}
```

**Subject:**
```
Ny besked fra {{from_name}} - Basic Sites
```

**Content:** (brug dette eller lav din egen)
```
Du har modtaget en ny besked fra kontaktformularen:

Navn: {{from_name}}
Email: {{from_email}}
Virksomhed: {{company}}

Besked:
{{message}}

---
Dette er en automatisk email fra Basic Sites kontaktformular
```

4. Klik "Save"
5. Kopier dit **Template ID** (fx: "template_xyz456")

## 4. Find din Public Key
1. Gå til "Account" eller "Integration"
2. Find din **Public Key** (fx: "user_AbCdEfGhIjKlMn")

## 5. Opdater index.html
Erstat følgende i index.html:

Linje ~399:
```javascript
emailjs.init("YOUR_PUBLIC_KEY"); // Erstat med din Public Key
```
Bliver til:
```javascript
emailjs.init("user_AbCdEfGhIjKlMn"); // Dit faktiske Public Key
```

Linje ~465-466:
```javascript
'YOUR_SERVICE_ID',  // Erstat med dit Service ID
'YOUR_TEMPLATE_ID',  // Erstat med dit Template ID
```
Bliver til:
```javascript
'service_abc123',   // Dit faktiske Service ID
'template_xyz456',  // Dit faktiske Template ID
```

## 6. Test
1. Åbn index.html i browser
2. Klik på "Send mig en email" knappen
3. Udfyld formularen og send
4. Check din email!

## Fejlfinding
- Hvis emails ikke sendes, check browser console for fejl
- Verificer at alle IDs er korrekte
- Check at din email service er aktiveret i EmailJS
- Sørg for at du ikke har overskredet gratis grænsen (200/måned)

## Alternativ: Brug mailto fallback
Hvis du ikke vil bruge EmailJS, virker formularen stadig med mailto: som åbner brugerens email program.