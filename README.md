# SwarnKosh Jewellery POS — Official Language & Translations Repository

This public repository hosts translation sources, available translations, invoice labels, number words, and numeral symbols for the **SwarnKosh Jewellery POS & Billing System**.

## Translation coverage and updates

The workbooks include all 3607 app texts and 121 invoice labels in the current source catalog. Marathi and Hindi are partially translated; blank translations fall back to English. Catalog checks verify coverage and placeholders, not linguistic quality or every possible runtime string.

To update an existing language, edit only its **Translation** column. Keep sheet names, Section, Key, and {placeholders} unchanged. Upload the workbook and update that language's version and updatedAt in index.json. In the app, use **Sync with GitHub & Excel → Refresh → Update & Sync**. Updates are applied on request, not automatically on every startup. A failed save leaves the installed version unchanged.

When app source texts change, run `npm run translations:generate` in the app project, then `npm run translations:check`. Generation preserves existing nonblank Marathi/Hindi translations in the local workbooks, so copy your latest edited workbooks back here before regenerating. Review index.json before publishing: generation resets its entries to the three built-in languages and the app version.

The repository URL is configured at app build time. Updating workbooks at the same URL does not require an app rebuild; changing the URL does.

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
   Change cell **B3** on the **Instructions** sheet to the new language ID (e.g. `gu-IN`), so importing it does not overwrite English.
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
     "wordsLanguage": "en",
     "version": "1.0.0",
     "updatedAt": "2026-09-27",
     "description": "સંપૂર્ણ ગુજરાતી ભાષા પેક"
   }
   ```
4. Commit and push your changes to GitHub. Open the language sync dialog and click Refresh, then Sync & Apply. New installations also fetch the language list during initial language selection. Use the Number words sheet for custom vocabulary; wordsLanguage supports only en, mr, or hi as a base converter.
