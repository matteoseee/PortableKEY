[![Release](https://img.shields.io/github/v/release/matteoseee/PortableKEY)](https://github.com/matteoseee/PortableKEY/releases) [![License](https://img.shields.io/github/license/matteoseee/PortableKEY)](LICENSE)


# 🔐 PortableKEY

**EN English**

**The standalone portable password manager**

PortableKEY requires no installation, no account, no internet but only a browser. Open it, use it, carry it with you.

<img width="1195" height="427" alt="image" src="https://github.com/user-attachments/assets/3030a66f-75ad-4d03-aceb-d26b4b9ecad7" />

---

## 🕵️ How it works?

**Passwords are stored only inside an AES-256 encrypted .pwm file. The master password is never stored and is intentionally forgotten after the file is created or opened** .

<img width="1007" height="265" alt="image" src="https://github.com/user-attachments/assets/8fe62066-0dd1-446d-b17f-c0ec106159bf" />

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

Want to check that it sends nothing over the network? Open the file and search for `fetch` or `XMLHttpRequest`: you won't find them. On top of that, a Content Security Policy makes the browser itself refuse any network access from the page.

---

## 🧭 At a glance

- 🧳 **Truly portable**: one file, zero dependencies. USB stick, shared folder, external drive.
- 🔌 **Works offline**: no network requests, no telemetry.
- 🛡️ **AES-256-GCM encryption**: the archive is encrypted with a key derived from your password (PBKDF2-SHA256, 1,000,000 iterations), with a 12-character minimum for the encryption password.
- 🧠 **Password forgotten right after use**: it isn't saved in the file or in the browser. Keeping it safe is up to you.
- 👁️ **Readable, unencrypted code**: inspect it with any text editor.
- 🔄 **Import/export without lock-in**: CSV and XLSX in (KeePass exports supported); TXT, CSV, XLSX and `.pwm` archive out.
- 📊 **Security summary**: MFA, weak and reused passwords, exposure by email, expirations and password age.
- 🌍 **Italian and English**, with a clean interface.
- ❓ **Guide**, on up-right corner there's always accessible guide in case you have any doubts.
- 🌙 **Dark theme**, now with Light or Dark theme switch
- ⏱️ **Auto-lock** after 3 minutes of inactivity.
- 🔑 **Help with strong passwords**: a strength indicator and a generator of random 8-word passphrases (about 80 bits).
- 🧱 **Passwords stay encrypted in memory** while the archive is open (best effort), and a revealed password hides again after 15 seconds.
- 🧯 **Content Security Policy**: the browser itself blocks every network request from the page.

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
- Eye button to reveal a password: it hides again by itself after 15 seconds
- Exported files are named with date and time (`password-YYYY-MM-DD_HH-MM.ext`), so you can keep progressive versions

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
- Encrypted CSV and XLSX exports contain a single text column that must not be edited.
- The archive format (`PWM2`) records its own version and iteration count in a header that is authenticated together with the data; archives from earlier versions (`PWM1`) can still be opened and are upgraded the next time you save.
- A **Content Security Policy** makes the browser block every network request from the page.
- While an archive is open, passwords are kept **encrypted in memory** with a random session key, and are decrypted only to show, copy, edit or export them. This is a best-effort extra layer, not a guarantee: whoever controls the browser or the page can still use the same functions.
- In unencrypted CSV and XLSX exports, values starting with `=`, `+`, `-` or `@` get a leading apostrophe to prevent **formula injection** in spreadsheets (it is removed again when you re-import the file).

### ⚠️ Good to know

- **Forgotten password = lost data.** There is no recovery, and that's the point.
- The HTML file **doesn't save by itself**: if you close the page without exporting, changes are lost (the browser warns you).
- **Unencrypted** exports write passwords in plain text: use them only when you really need to (the app warns you and asks for confirmation first).
- **Auto-lock:** after 3 minutes without activity the page releases the data (to reopen the archive you import it again with its password). If you have unsaved changes, to avoid losing them the data stays in memory but is hidden behind a lock screen until you save an encrypted archive or resume. Releasing data from the page does not guarantee physical erasure from RAM.
- Archives saved in the new format cannot be opened by older copies of PortableKEY: keep the old archive until you have checked the new one.
- No software can protect you from an already compromised computer (keyloggers, malware). Use PortableKEY on devices you trust.
- The project hasn't undergone an independent security audit. The code is right there, readable: if you do this for a living, **review it and tell us what you find**.
- Always download the file from a source you trust: a tampered copy is the real risk of any program, and here you can at least verify it.

---

## ✅ Verify your download

The SHA-256 hash of each release is published in the release notes on GitHub. Before using a copy of `PortableKEY.html`, compute its hash and compare it with the one on the release page:

- **Windows (PowerShell):** `Get-FileHash .\PortableKEY.html -Algorithm SHA256`
- **macOS / Linux:** `shasum -a 256 PortableKEY.html`

The two values must be identical. Take the reference hash from the release page on GitHub, not from the same place the file was handed to you: a matching hash only proves something if the hash itself comes from a trustworthy source.

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

**Can I open archives created by older versions?**
Yes. Older `.pwm` files (300,000 iterations) still open, and are saved in the new format the next time you save. The opposite doesn't work: older copies of the app can't read new archives.

**What does the password strength indicator tell me?**
It is a rough estimate in bits, not a guarantee. For the encryption password the best option is a random passphrase: the *Generate phrase* button creates 8 words (about 80 bits). Write it down: it is never stored.

---

## 🤝 Contributing

The project is a single file: reading it, understanding it and improving it is within everyone's reach.

- 🐛 Found a bug or a security issue? Open an *issue*.
- 💡 Have an idea? Propose it with a *pull request*.
- 🌍 Want to add a language? Just add a new entry to the translations dictionary.

Golden rule: **no external dependencies and no network requests**. If your change needs them, it isn't PortableKEY.

---

## 📄 License

PortableKEY is free software, released under the **GNU General Public License v3.0**. See the [LICENSE](LICENSE) file.

---

<p align="center"><b>PortableKEY</b><br>One file. Your code. Your keys. 🔑</p>
