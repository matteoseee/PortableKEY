[![Release](https://img.shields.io/github/v/release/matteoseee/PortableKEY)](https://github.com/UTENTE/REPOSITORY/releases) [![License](https://img.shields.io/github/license/matteoseee/PortableKEY)](LICENSE)


# 🔐 PortableKEY

**EN English**

**The standalone portable password manager**

**Passwords are stored only inside an AES-256 encrypted .pwm file. The master password is never stored and is intentionally forgotten after the file is created or opened** .

PortableKEY requires no installation, no account, no internet but only a browser. Open it, use it, carry it with you.

<img width="1195" height="490" alt="image" src="https://github.com/user-attachments/assets/b0d9cb3c-4dfa-4020-8727-e80083f3bc1a" />

---

## ✨ Open Source 2.0

Traditional open source tells you: *"the code is public, go download it, build it, install it."*

PortableKEY goes further ! Open `PortableKEY.html` in Notepad and read everything it does

There is no binary to trust, no obfuscated code, no build step that could hide something else. What you read is exactly what runs, line by line.

| | Typical password manager | PortableKEY |
|---|---|---|
| Installation | Yes | **None** |
| Verifiable code | After downloading and building the sources | **Right away, with a text editor** |
| External dependencies | Dozens | **Zero** |
| Internet connection | Often required | **Never** |
| Where your data lives | A service, an app, a database | **A file you control** |

Want to check that it sends nothing over the network? Open the file and search for `fetch` or `XMLHttpRequest`: you won't find them.

---

## 🧭 At a glance

- 🧳 **Truly portable**: one file, zero dependencies. USB stick, shared folder, external drive.
- 🔌 **Works offline**: no network requests, no telemetry.
- 🛡️ **AES-256-GCM encryption**: the archive is encrypted with a key derived from your password (PBKDF2-SHA256, 300,000 iterations).
- 🧠 **Password forgotten right after use**: it isn't saved in the file or in the browser. Keeping it safe is up to you.
- 👁️ **Readable, unencrypted code**: inspect it with any text editor.
- 🔄 **Import/export without lock-in**: CSV and XLSX in (KeePass exports supported); TXT, PDF, CSV, XLSX and `.pwm` archive out.
- 📊 **Security summary**: MFA, weak and reused passwords, exposure by email, expirations and password age.
- 🌍 **Italian and English**, with a clean white interface.
- ❓ **Guide**, on up-right corner there's always accessible guide in case you have any doubts.
- 🌙 **Dark theme**, now with Light or Dark theme switch

---

## 🚀 How to use it

1. **Download** `PortableKEY.html`.
2. **Open** it with your browser (double-click).
3. **Add** your entries by hand, or **import** a CSV/XLSX file with the *Import* button.
4. **Save** with *Save / Export*: choose an encryption password, keep it yourself, and get your `.pwm` archive.

To reopen the archive: *Import*, pick the file, enter the password. That's it.
 
> 💡 Inside the app you'll find a **Guide** with a downloadable import template (CSV or XLSX) ready to fill in.

---

## 🧰 What it can do

**Entry management**
- Title, group, email, username, password, URL, notes
- **MFA** column to track where you've enabled multi-factor authentication
- **Date added** and **expiry date**, both optional
- Search, A→Z sorting on every column, combinable dropdown filters on each column, random 20-character password generator
- One-click copy: the clipboard is cleared after 20 seconds

<img width="1199" height="781" alt="Screenshot 2026-10-25 123755" src="https://github.com/user-attachments/assets/53705ba2-0819-436b-82ef-2fbd9234f343" />


**Security summary** 📊

A dedicated tab gives you the full picture:
- percentage of accounts with **MFA**
- percentage of **weak** passwords (under 12 characters) and **reused** ones
- **exposure by email address and domain**: how many accounts fall if a single mailbox is compromised
- **username report**: which usernames are reused across accounts
- **expiry report**: expired, expiring within 30 and 90 days
- **age report**: how long it has been since you changed certain passwords

<img width="1189" height="705" alt="Screenshot 2026-10-25 123816" src="https://github.com/user-attachments/assets/a50aecf0-952f-4de5-8de6-749041c385a4" />


<img width="1187" height="901" alt="Screenshot 2026-10-25 123846" src="https://github.com/user-attachments/assets/6866a918-2183-4f8f-8ff6-ae2f0be7450f" />

---

## 🔒 Security: how it works, no fluff

- Encryption uses your browser's **Web Crypto API**, the same technology that protects HTTPS connections. No third-party libraries.
- Every encrypted save generates fresh random values: saving the same archive twice produces two different files.
- Encrypted files don't state which algorithm they use: they contain only encrypted data.
- Encrypted CSV and XLSX exports contain a single text column that must not be edited; the encrypted PDF is an archive copy and can't be re-imported.

### ⚠️ Good to know

- **Forgotten password = lost data.** There is no recovery, and that's the point.
- The HTML file **doesn't save by itself**: if you close the page without exporting, changes are lost (the browser warns you).
- **Unencrypted** exports write passwords in plain text: use them only when you really need to.
- No software can protect you from an already compromised computer (keyloggers, malware). Use PortableKEY on devices you trust.
- The project hasn't undergone an independent security audit. The code is right there, readable: if you do this for a living, **review it and tell us what you find**.
- Always download the file from a source you trust: a tampered copy is the real risk of any program, and here you can at least verify it.

---

## 📁 Supported formats

| | Import | Export | Encryptable |
|---|:---:|:---:|:---:|
| `.pwm` archive | ✅ | ✅ | ✅ (always) |
| CSV | ✅ | ✅ | ✅ |
| XLSX | ✅ | ✅ | ✅ |
| TXT | ✅ (if encrypted) | ✅ | ✅ |

Import detects encrypted files on its own and asks for the password. Column headers can be in Italian or English, including those from KeePass exports.

---

## 🌐 Compatibility

Works with modern, up-to-date browsers (Chrome, Edge, Firefox, Safari). No plugins, no extensions, no apps to install.

---

## ❓ Quick questions

**Where are my passwords stored?**
Only where you save them, in the file you export. While you use it they stay in the page's memory and disappear when you close it.

**Can I run it from a USB stick?**
Yes, that's what it's for. Remember to export the updated archive before closing.

**Does it autofill forms or integrate with the browser?**
No, on purpose. Fewer features, smaller attack surface, more code you can read in one evening.

**Does it open KeePass `.kdbx` files?**
No. You can export from KeePass to CSV and import that file into PortableKEY.

---

## 🤝 Contributing

The project is a single file: reading it, understanding it and improving it is within everyone's reach.

- 🐛 Found a bug or a security issue? Open an *issue*.
- 💡 Have an idea? Propose it with a *pull request*.
- 🌍 Want to add a language? Just add a new entry to the translations dictionary.

Golden rule: **no external dependencies and no network requests**. If your change needs them, it isn't PortableKEY.

---

<p align="center"><b>PortableKEY</b><br>One file. Your code. Your keys. 🔑</p>
