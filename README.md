# Salesforce Data Model — Chrome Extension

A powerful Chrome extension that lets Salesforce administrators and developers browse, inspect, and export the complete data model of any Salesforce org — directly from the browser.

![Manifest V3](https://img.shields.io/badge/Manifest-V3-blue)
![Chrome Web Store](https://img.shields.io/badge/Platform-Chrome-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

---

## Features

### Object Metadata Browser
- **Fields** — View field label, API name, type, required, unique, external ID, length, precision, scale, and picklist dependency status. Click any field label to jump to its setup page.
- **Record Types** — List all record types with clickable IDs. Inspect assigned picklist values per record type.
- **Page Layouts** — View page layouts associated with the selected object.
- **FlexiPages** — Browse Lightning pages linked to the object.
- **Validation Rules** — View rule name, active status, description, formula, error message, and error display field.
- **Field Sets** — View field set members, labels, and descriptions.

### Picklist Dependency Viewer
- Visual matrix showing which dependent picklist values are available for each controlling value.
- Accessible from the "Dependency" column in the Fields tab.

### Excel Export
- One-click export of all metadata into a multi-sheet `.xls` workbook.
- Includes sheets for Fields, Record Types, Layouts, FlexiPages, Validation Rules, Field Sets, and Record Type picklist assignments.
- Dependent picklist mappings are exported as separate sheets with internal hyperlinks.

### Customizable UI
- Configure which columns are visible and their display order for each tab.
- Show or hide entire tabs from the Settings page.
- Preferences are saved locally and persist across sessions.

---

## Installation

### From Chrome Web Store
1. Visit the [Salesforce Data Model](https://chrome.google.com/webstore/detail/salesforce-data-model) listing.
2. Click **Add to Chrome**.

### Manual / Developer Install
1. Clone or download this repository.
2. Open `chrome://extensions` in Chrome.
3. Enable **Developer mode** (toggle in the top-right).
4. Click **Load unpacked** and select the project folder.

---

## Usage

1. **Log in** to your Salesforce org in Chrome.
2. **Click the extension icon** in the toolbar (or find it in the extensions menu).
3. The extension opens in a new tab and detects your active Salesforce session.
4. **Search or select an object** from the dropdown.
5. Browse metadata across the tabbed interface.
6. Click **Export Excel** to download the full data model as a spreadsheet.

---

## Project Structure

```
├── manifest.json          # Chrome extension manifest (V3)
├── background.js          # Service worker — Salesforce API calls
├── popup.html             # Main popup UI (tab-based page)
├── popup.js               # Popup logic — rendering, export, events
├── popup.css              # Popup styles
├── app.html               # Full-tab version of the popup
├── settings.html          # Settings page UI
├── settings.js            # Settings logic — column/tab configuration
├── settings.css           # Settings styles
├── dependency.html        # Dependency matrix viewer
├── dependency.js          # Dependency matrix logic
├── icons/                 # Extension icons (16, 48, 128)
├── PRIVACY_POLICY.md      # Privacy policy
└── README.md              # This file
```

---

## Permissions

| Permission | Purpose |
|---|---|
| `cookies` | Read the Salesforce `sid` session cookie for API authentication |
| `storage` | Save user preferences (column order, tab visibility) |
| `tabs` | Open setup pages and the extension in new tabs |
| `Host permissions` | Make API requests to `*.salesforce.com`, `*.force.com`, etc. |

The extension does **not** use `activeTab`, does **not** expose `web_accessible_resources`, and does **not** persist session tokens in storage.

---

## Security

- **Manifest V3** with service worker architecture.
- **No `innerHTML`** — all DOM rendering uses safe APIs (`textContent`, `createElement`).
- **No token persistence** — the Salesforce `sid` is read from cookies at runtime and never stored.
- **No external requests** — the extension communicates only with your Salesforce org.
- **Minimal permissions** — only the permissions strictly required for functionality.

---

## Privacy

See [PRIVACY_POLICY.md](PRIVACY_POLICY.md) for the full privacy policy.

**In short:** The extension is read-only, does not collect analytics, does not share data with third parties, and communicates only with your Salesforce org.

---

## Support

If you find this extension useful, consider supporting the developer:

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-Support-orange)](https://buymeacoffee.com/virajrana)

---

## Contributing

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/my-feature`).
3. Commit your changes (`git commit -m "Add my feature"`).
4. Push to the branch (`git push origin feature/my-feature`).
5. Open a Pull Request.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Contact

**Developer:** Viraj Rana
**Email:** viraj.rana55@gmail.com
**GitHub:** [https://github.com/virajrana55](https://github.com/virajrana55)
