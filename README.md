# SwarnKosh Jewellery POS — Official Language & Translations Repository

This public repository hosts official translations, invoice labels, number words, and numeral symbols for the **SwarnKosh Jewellery POS & Billing System**.

---

## 📁 Repository Structure

```
├── index.json          # Master language index manifest
├── marathi.xlsx        # Marathi (मराठी) translation workbook
├── hindi.xlsx          # Hindi (हिन्दी) translation workbook
├── english.xlsx        # English reference workbook
└── README.md           # Documentation and setup instructions
```

---

## 🚀 How to Host & Use This Repository

1. **Create a Public GitHub Repository**:
   Create a new public repository on GitHub (e.g. `https://github.com/your-username/jewellers-pos-translations`).

2. **Push the Files to the `main` branch**:
   Copy the contents of this folder into your repository and push to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Initial language workbooks for Marathi, Hindi, and English"
   git branch -M main
   git remote add origin https://github.com/your-username/jewellers-pos-translations.git
   git push -u origin main
   ```

3. **Configure Your App `.env`**:
   In your SwarnKosh POS application, add the repository URL to `.env`:
   ```env
   VITE_TRANSLATIONS_REPO_URL=https://raw.githubusercontent.com/your-username/jewellers-pos-translations/main
   ```
   *(Note: You can also specify `https://github.com/your-username/jewellers-pos-translations` and the app will automatically resolve the raw URL.)*

---

## 🌐 Adding New Languages

To add a new language (e.g. Gujarati, Kannada, Tamil, Telugu, Bengali):
1. Copy `english.xlsx` to `<language>.xlsx` (e.g. `gujarati.xlsx`).
2. Open in Excel and update the **Translation** column in each sheet:
   - **Text translations**: Translate labels and interface messages.
   - **Number words**: Provide words for numbers 0–99, hundreds 100–900, currency (रुपये), subunit (पैसे), and scale words.
   - **Digits**: Provide regional digit symbols (e.g. ૦, ૧, ૨, ૩, ૪...).
3. Add the language entry to `index.json`:
   ```json
   {
     "id": "gu-IN",
     "name": "Gujarati",
     "nativeName": "ગુજરાતી",
     "file": "gujarati.xlsx",
     "direction": "ltr",
     "wordsLanguage": "gu",
     "version": "1.0.0",
     "updatedAt": "2026-09-27",
     "description": "સંપૂર્ણ ગુજરાતી ભાષા પેક"
   }
   ```
4. Commit and push your changes to GitHub. The app will immediately detect the new language on startup and in Settings!
