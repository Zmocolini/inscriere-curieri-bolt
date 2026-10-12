# 🛵 Pagina Web de Înscriere Curieri Bolt Food (Optimizată 100% Mobil & Vercel)

Această aplicație web înlocuiește definitiv **Google Forms**, eliminând complet:
- ❌ Cerința obligatorie de conectare cu cont Google (permite înscrierea oricărui candidat, inclusiv utilizatori de Yahoo, iCloud etc.).
- ❌ Erorile de încărcare a buletinului pe telefoane **Samsung** (*Smart Anti-Tracking*).
- ❌ Erorile de încărcare pe **iPhone** (*Safari cross-site prevention*).
- ❌ Erorile din browserul intern **WhatsApp / Facebook / Instagram**.

---

## ⚡ Caracteristici Principale

1. **Design Mobile-First Stil Bolt Food:**
   - Paletă de culori oficială Bolt Food (verde vibrant `#00D287`, fundal întunecat elegant, carduri albe cu finisaj modern).
   - Butoane mari, prietenoase pentru degetul mare pe ecran mobil.
   - 3 carduri tapabile pentru selecția vehiculului: 🚗 Mașină, 🛵 Scuter / Moto, 🚲 Bicicletă.
   - Dropdown nativ cu **cele 30 de orașe oficiale Bolt Food** din România.

2. **Compresie Automată Client-Side a Pozei de Buletin (HTML5 Canvas):**
   - Când candidatul face o poză cu camera telefonului (4K de 5–10 MB), browserul o redimensionează și o comprimă automat în **0.1 secunde** la un fișier JPEG clar de aproximativ **800 KB – 1.2 MB**.
   - Încărcarea se face în sub **1 secundă**, chiar și pe conexiuni mobile 4G/3G slabe, cu zero blocaje sau timeout-uri.
   - Suportă captură directă din camera foto (`📸 Fă Poză Acum`) sau selecție din galerie (`📁 Alege din Galerie`).
   - Formate acceptate: **JPG, PNG, HEIC, PDF** (până la 15 MB).

3. **Arhitectură Securizată Vercel Serverless:**
   - Datele sunt trimise către ruta `/api/submit` (funcție serverless Vercel Node.js).
   - Funcția transmite cererea securizat către Webhook-ul **Google Apps Script & Google Sheets**.
   - Candidatul apare instantaneu în **Google Sheets** (cu status `NOU`).
   - Robotul Python preia automat datele în câteva secunde și trimite pe **Telegram** cardul interactiv cu butoanele `[ ✅ Confirmă și Trimite la Bolt ]` și `[ ❌ Respinge ]`!

---

## 📁 Structura Fișierelor

```
inscriere-curieri/
├── api/
│   └── submit.js       # Vercel Serverless Function (proxy securizat către Google Apps Script)
├── public/
│   ├── index.html      # Landing page + formular optimizat mobil
│   ├── styles.css      # Design modern, responsive, stil Bolt Food
│   └── app.js          # Validare client, compresie Canvas, preview foto & submit
├── vercel.json         # Configurație rutare & CORS pentru Vercel
├── package.json        # Metadate proiect Vercel
└── README.md           # Ghidul de instalare și publicare
```

---

## 🚀 Ghid Pas cu Pas: Publicare Gratuită pe Vercel (sub 3 minute)

### Metoda 1: Prin Vercel CLI (Cea mai rapidă din calculator)

1. Deschide **PowerShell** sau **Command Prompt** în folderul proiectului:
   ```powershell
   cd C:\balante21\inscriere-curieri
   ```

2. Instalează Vercel CLI (dacă nu îl ai deja):
   ```powershell
   npm install -g vercel
   ```

3. Rulează comanda de conectare și publicare:
   ```powershell
   vercel
   ```
   - Te va întreba dacă vrei să faci login în browser (apeși Enter și te autentifici pe Vercel).
   - La întrebarea `Set up and deploy?` răspunzi: `Y` (Yes).
   - La `Which scope do you want to deploy to?` alegi contul tău Vercel.
   - La `Link to existing project?` răspunzi: `N` (No).
   - La `What's your project's name?` pui: `inscriere-curieri-bolt` (sau orice nume dorești).
   - La `In which directory is your code located?` apeși `Enter` (`./`).
   - La `Want to modify these settings?` răspunzi: `N` (No).

4. Pentru publicarea pe domeniul final de producție:
   ```powershell
   vercel --prod
   ```

5. **GATA!** Vercel îți va afișa linkul tău public (exemplu: `https://inscriere-curieri-bolt.vercel.app`), pe care îl poți trimite oricărui candidat pe WhatsApp sau Facebook!

---

### Metoda 2: Prin GitHub & Vercel Dashboard (Fără terminal)

1. Creează un depozit (Repository) nou pe [GitHub.com](https://github.com) (privat sau public).
2. Încarcă fișierele din folderul `C:\balante21\inscriere-curieri` pe GitHub.
3. Intră pe [Vercel.com](https://vercel.com) și conectează-te cu contul GitHub.
4. Apasă pe butonul albastru **„Add New...”** ➡️ **„Project”**.
5. Selectează depozitul tău de pe GitHub și apasă **„Import”**.
6. Apasă direct pe **„Deploy”** (nu este nevoie să modifici nicio setare).
7. În aproximativ 20 de secunde, pagina ta este online 24/7!

---

## ⚙️ Variabile de Mediu (Opțional)

Dacă dorești să configurezi URL-ul Webhook-ului prin panoul Vercel (fără a folosi valoarea implicită din cod), poți adăuga în Vercel la **Settings ➡️ Environment Variables**:

| Nume Variabilă | Valoare Implicită |
| :--- | :--- |
| `GOOGLE_APPS_SCRIPT_URL` | `https://script.google.com/macros/s/AKfycbwtBI0Vh8IPDgBO0Yf5OsgqBjQ1slwdxLShpVocyhojpePGKtOE5G3AjndJiwpp72pR/exec` |
| `GOOGLE_APPS_SCRIPT_TOKEN` | `bolt_fleet_secure_2026` |

---

## 🌐 Domeniu Personalizat (Opțional)

Dacă deții un domeniu propriu (de exemplu: `curieribolt.ro` sau un subdomeniu `inscriere.flotata.ro`):
1. În panoul de control Vercel al proiectului, mergi la **Settings** ➡️ **Domains**.
2. Introdu domeniul tău și apasă **Add**.
3. Urmează instrucțiunile DNS (setare înregistrare CNAME sau A record).
4. Vercel va genera automat certificat SSL HTTPS gratuit!
