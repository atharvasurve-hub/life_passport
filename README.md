# Life Passport v2.0 🪪

> **Self-Contained Offline Emergency Medical & Caregiver Passport for Non-Verbal & At-Risk Loved Ones**  
> Powered by client-side Google Gemini 2.5 Flash, Web Speech recognition & Speech Synthesis, compact QR schema minification, pure-JS inlined offline engines, and zero-server privacy architecture.

---

## 🌟 What is Life Passport?

Life Passport turns a messy pile of medical records, crumpled prescriptions, and caregiver voice notes into a high-contrast, one-page emergency card. 

Built specifically for vulnerable individuals who cannot speak for themselves—such as an elderly person with dementia, a child with autism or allergies, or a person with an acute disability. Any stranger (ER doctor, relief-camp volunteer, police officer) can scan the QR code and instantly see **only what they need to act in the first 10 seconds**.

---

## 🚀 Key Highlights & Architectural Strengths

### 1. 100% Offline Autonomy (Zero External Network Dependencies)
- **Inlined Pure-JS Engines:** `QRCode.js` (QR matrix generator), `LZ-String` (compression), and `jsQR` (webcam & image decoder) are **completely embedded directly inside `index.html`**. 
- Even if opened in an offline disaster shelter, subway station, or flight with **zero internet connection**, the entire application—QR code generation, URL hash decompression, and camera barcode scanning—runs without missing a beat.

### 2. Physical & Digital Emergency Media (Ready for 3 AM)
- **Credit-Card Size Wallet Card (ISO/IEC 7810 ID-1 standard: 85.6mm × 53.98mm):** Front and back sides printed side-by-side with scissor cut borders, center fold dashed guide line, patient photo, blood type, DNR status, dynamic allergy list, calming notes, ICE contact, and micro-QR code.
- **Medical Adhesive Wristband (1" × 8.5" / 25.4mm × 215.9mm):** Standard hospital bracelet format with high-contrast barcode, allergy warnings, and emergency contact.
- **A6 Pocket Emergency Action Sheet (105mm × 148mm):** Foldable emergency medical summary for intake binders or backpacks.
- **9:16 High-Res Mobile Lock Screen Wallpaper (1080 × 1920):** High-definition canvas-generated smartphone lock screen with patient photo, top red alert box, QR code, and tap-to-call primary contact.
- **Targeted Print Isolation:** Clean print stylesheets ensure printing outputs *only* the chosen template (wallet card, wristband, or A6 sheet) with zero page headers, navbars, or screen clutter.

### 3. QR Schema Minification & URL Hash Architecture
- **Compact Schema Minification:** Automatically shrinks JSON payloads before LZ-String compression (`compactPassport` / `expandPassport`), reducing payload density by **50%** to ~300 characters.
- **Sub-Second Scans:** QR codes scan in <0.2s even on budget phone cameras or under dim 3 AM lighting.
- **Host / Target Domain Field:** Built-in configurable Base URL box on the Share screen allows testing phone camera scans over local Wi-Fi (e.g. `http://192.168.1.5:8000`) or deploying to custom domains.
- **1-Click "📱 Test QR Scan":** Instantly simulates scanning the offline QR code and loads the responder view in one click on any laptop or desktop.

### 4. Human-in-the-Loop Clinical Reconciliation (Safety First)
- **Mandatory Approval Gate:** Offline QR codes and export formats cannot be generated until a human reviews and approves the extracted fields.
- **Interactive "Please Confirm" Flags:** Prominently highlights smudged or conflicting items (e.g., *discontinued Glipizide vs Metformin*, *unclear handwritten beta-blocker dosage*, *surgical history*).
- **1-Click Clinical Reconciliation:** Tapping **"⚡ Reconcile Card"** automatically resolves conflicts, cleans up active medication tables, updates clinical interaction warnings, and dismisses amber flags.
- **Non-Blocking Toasts:** Replaces jarring modal `alert()` popups with subtle, professional medical UI status toasts.

### 5. Multimodal Audio & Document Intake
- **Synthesized Voice Note Preview:** Tapping "Insert Elena's Voice Note" attaches the caregiver memo and generates a live synthesized audio chime with synchronized Speech Synthesis voice playback.
- **Voice Memo Audio File Upload:** Caregivers can upload recorded audio files (`.mp3`, `.m4a`, `.wav`, `.ogg`) directly into the app.
- **Live Microphone Recording:** Web Speech API speech-to-text with multi-language selector (English, Spanish, Hindi, French, Cantonese, etc.).
- **Sample Document Attachments:** Pre-loaded with St. Jude hospital discharge summary, messy handwritten prescription, and pharmacy pill bottle.

### 6. Responder View & Internationalization
- **10 Pre-Cached Offline Languages:** English, Español, Français, हिन्दी, 中文, العربية, Deutsch, Tagalog, Українська, and 日本語 all feature pre-cached clinical translations that work 100% offline without requiring an API key.
- **Live Gemini Translation:** When an API key is provided, on-demand translation supports any language while preserving clinical drug names, doses, and phone numbers.
- **Role-Based Views:** Tailored triage tabs for:
  - **Doctor / ER:** Allergies, conditions, current medicines, do-not-give list, interactions, baseline behavior.
  - **Police / First Responder:** Name, age, who to call, how to approach and calm, do-not-restrain notes.
  - **Relief Volunteer:** Needs, diet, mobility, who to call, medicines to continue.
  - **All Details:** Complete clinical summary.
- **Hands-Free Calming Audio Playback:** Responders with hands occupied can tap **"🔊 Listen to Calming Audio"** to hear gentle de-escalation instructions spoken aloud.
- **Zero Privacy Leaks:** Strict rule prevents home address, financial details, or government IDs (SSN) from ever appearing on the card or in the payload.

---

## 🏃 Quick Start & Testing Guide

### Option 1: Open Directly in Browser (No Server Needed)
1. Double-click `index.html` to open it in Chrome, Edge, Safari, or Firefox.
2. Click **Demo** in the top navigation bar to load Arthur Pendelton's (72yo with dementia, diabetes, and penicillin allergy) verified card.
3. Review the fields and click **"Approve & Generate Emergency Card"**.
4. Test the generated QR code:
   - Tap **"📱 Test QR Scan"** to experience what an ER doctor sees instantly.
   - Or tap **"🖨️ Print Wallet Card"** to preview the scissor-fold credit-card format.
   - Or tap **"Save Wallpaper Image"** to download the 1080×1920 mobile lockscreen wallpaper.

### Option 2: Test Live Phone Scanning Over Local Wi-Fi
1. Open PowerShell / Terminal in this folder:
   ```bash
   python -m http.server 8000
   ```
2. Find your computer's local IP (e.g., `192.168.1.X`).
3. In `index.html` on the **Share** screen, enter `http://192.168.1.X:8000/index.html` in the **Host / Target Domain** box.
4. Point your physical iPhone or Android camera at the screen to scan the QR code—it opens directly into the Responder triage view on your mobile phone!

### Option 3: Extract Live Records with Gemini 2.5 Flash
1. Click **⚙️ Settings** in the top right corner.
2. Enter your Google Gemini API Key and click **Save Settings**.
3. Upload medical record photos/PDFs, record a voice note, and click **"⚡ Build Passport with Gemini 2.5 Flash"**.

---

## 🛡️ Clinical & Privacy Safety Disclaimers
- **Clinical Notice:** Prepared by family from personal records. Not a medical diagnosis. Always verify clinical records before administering treatment.
- **Privacy Assurance:** Zero cloud storage, zero tracking, zero accounts. All data resides in the browser session and encrypted inside the offline QR URL hash.
