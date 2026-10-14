**Languages**: [English](README.md) | [简体中文](docs/zh-CN/README.md)

---

# ReviewWise — AP Question Analyzer

A Chrome extension designed for AP students that automatically analyzes multiple-choice questions on College Board AP Classroom using Chrome's built-in Gemini Nano AI. It identifies student misconceptions and provides Socratic guidance to help students self-correct their errors.

---

## ✨ Core Features

### 🎯 Smart Analysis
- **Subject Detection**: Automatically identifies 13 AP subjects, AI uses subject-specific terminology and frameworks
- **Misconception Identification**: Deep analysis based on College Board official explanations (A-D options)
- **Socratic Guidance**: Guides students to think independently rather than giving direct answers
- **LaTeX Rendering**: Perfect display of mathematical formulas and physics symbols

### 📚 Misconception Bank
- **Smart Deduplication**: Automatically merges identical questions and tracks error counts
- **Subject Classification**: Filter mistakes by AP subject
- **One-Click Export**: Export as JSON/CSV format
- **Local Storage**: Data saved locally in browser for privacy

### 🌐 Community Features (Optional)
- **Feedback System**: 👍 👎 feedback on analysis quality
- **Community Recommendations**: View analyses with high approval ratings (helpful ratio > 60%)

### ⚡ Automation
- **Auto-Scan**: Automatically analyzes when visiting question pages (can be disabled via popup)
- **Result Caching**: Same questions won't be re-analyzed (1-hour validity)
- **Floating Panel**: Non-intrusive analysis panel that doesn't interfere with webpage content

---

## 🎓 Supported AP Subjects

This extension supports automatic detection of 13 AP subjects:

| AP Subject ID | Subject Name | Icon |
|---------------|--------------|------|
| 7 | AP Chemistry | 🧪 |
| 8 | AP Computer Science A | 💻 |
| 11 | AP Microeconomics | 💹 |
| 13 | AP English Literature and Composition | 📖 |
| 26 | AP Calculus BC | ∑ |
| 29 | AP Physics C: Mechanics | 🧲 |
| 30 | AP Psychology | 🧠 |
| 33 | AP Statistics | ∑ |
| 78 | AP Physics C: Electricity and Magnetism | 🧲 |
| 93 | AP Physics 2 | 🧲 |
| 94 | AP Seminar | 📖 |
| 103 | AP Computer Science Principles | 💻 |
| 117 | AP Precalculus | ∑ |

*Subject detection is based on AP Classroom URL (e.g., `apclassroom.collegeboard.org/93/...` corresponds to AP Physics 2)*

---

## 📥 Installation

### Prerequisites
- **Chrome Browser Version**: 138 or higher
- **Enable Gemini Nano**:
  1. Visit `chrome://flags`
  2. Search for "Prompt API for Gemini Nano"
  3. Set to "Enabled"
  4. Restart browser

### Installation Steps
1. Download or clone this repository
2. Open `chrome://extensions/`
3. Enable "Developer mode" in the top right
4. Click "Load unpacked extension"
5. Select the `dist/` folder
6. Extension installed!

### Optional: Supabase Configuration

The extension works perfectly without any configuration. However, if you want to enable cloud sync features (recommended analyses, user feedback statistics), you can configure Supabase:

1. See [SETUP_SUPABASE.md](SETUP_SUPABASE.md) for detailed instructions
2. Copy `supabase-config.example.js` to `supabase-config.js` and fill in your credentials
3. Run `npm run build` to rebuild the extension

**Note**: Without Supabase configuration, the extension runs in local-only mode with all core features available.

---

## 🚀 Usage Guide

### Auto-Analysis Mode (Recommended)
1. Visit an AP Classroom question page (e.g., `apclassroom.collegeboard.org/93/...`)
2. Extension automatically detects subject, extracts question, and calls AI analysis
3. Floating panel displays analysis results:
   - Subject icon (e.g., 🧲 AP Physics 2)
   - Misconception diagnosis
   - Feedback buttons (👍 👎)
   - Save button (☆ Save)

### Manual Analysis Mode
1. Click extension icon to open popup
2. Turn off "Auto-scan" toggle
3. Visit question page, then click "Analyze Current Question" button

### View Misconception Bank
1. Click extension icon to open popup
2. Click "View Misconceptions"
3. View all saved mistakes in a new tab
4. Filter by subject, export, or delete

---

## 🎨 UI Preview

### Floating Analysis Panel
```
┌──────────────────────────────────────┐
│ 🧲 AP Physics 2             − ↻ ×    │
├──────────────────────────────────────┤
│ 💡 Misconception Identified          │
│                                      │
│ If the magnet were removed, the     │
│ paper clip would no longer attract  │
│ others, so the clip is only         │
│ temporarily magnetized rather than  │
│ a permanent magnet.                 │
│                                      │
│ 👍 👎 ☆ Save                         │
└──────────────────────────────────────┘
```

---

## 🔒 Privacy & Security

- ✅ **Local AI**: Uses Chrome's built-in Gemini Nano, all analysis done locally on device
- ✅ **No Network Requests**: Core functionality doesn't depend on external servers
- ✅ **Local Data**: Misconception bank stored locally in browser (`chrome.storage.local`)
- ✅ **Anonymous Feedback**: Supabase only stores URL hashes (SHA-256), not original URLs

---

## 🛠️ Development

### Build
```bash
# Install dependencies
npm install

# Build extension (outputs to dist/)
npm run build
```

### Debug AI
1. Open `chrome://extensions/`
2. Find "Question Analyzer" → Click "background page"
3. View `[AI Prompt]` collapsed logs in Console
4. Verify subject detection and A-D explanation extraction

---

## 📖 Documentation

- **[ARCHITECTURE.md](ARCHITECTURE.md)** - System architecture (detailed AI processing pipeline)
- **[TECHNICAL_DOCS.md](TECHNICAL_DOCS.md)** - Technical documentation (detailed prompt engineering)
- **[CODE_STRUCTURE.md](CODE_STRUCTURE.md)** - Code structure (AI-related files highlighted)

---

## 🤝 Contributing

Issues and Pull Requests are welcome!

---

## 📄 License

Apache 2.0
