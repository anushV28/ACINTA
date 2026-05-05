# 🌿 MindEase — Mental Wellness Chatbot

A free, rule-based mental wellness chatbot that runs entirely in the browser. No server, no API key, no cost. Just open the HTML file and it works.

---

## 📁 Project Structure

```
mindease/
├── index.html       ← the entire chatbot (rename from mindease-chatbot.html)
└── README.md        ← this file
```

---

## 🚀 How to Run Locally

1. Download `mindease-chatbot.html`
2. Double-click it — it opens in any browser
3. That's it. No installation needed.

---

## 🌐 How to Deploy (Free)

### Option A — Netlify (easiest, 30 seconds)
1. Rename the file to `index.html`
2. Go to [netlify.com](https://netlify.com) and sign up free
3. Drag and drop `index.html` onto the Netlify dashboard deploy zone
4. You get a live URL instantly (e.g. `https://mindease.netlify.app`)
5. Optional: go to **Site settings → Change site name** to customise the URL

### Option B — GitHub Pages
1. Go to [github.com](https://github.com) and create a new **public** repository named `mindease`
2. Upload `index.html` (renamed from `mindease-chatbot.html`)
3. Go to **Settings → Pages → Source → Deploy from branch → main**
4. Your live URL: `https://yourusername.github.io/mindease`

---

## ✏️ How to Customise

Open `index.html` in any text editor (VS Code recommended).

### Change the chatbot name
Find in the HTML:
```html
<h1>MindEase</h1>
<p>A safe space to talk about how you feel</p>
```
Replace with your own name and tagline.

### Change colours
All colours are defined in the `<style>` block at the top. Key values to change:

| What | CSS selector / property | Default value |
|---|---|---|
| Header background | `#mh` → `background` | `#0a0a1a` to `#1a3a6e` |
| Page background | `#mm` → `background` | `#0d0d1a` |
| User chat bubble | `.xm.u .xb` → `background` | `#1a3a8f` |
| Bot chat bubble | `.xm.b .xb` → `background` | `#111827` |
| Send button | `#msb` → `background` | `#1d4ed8` |
| Quick reply chips | `.xk` → `border-color` / `color` | `#2563eb` / `#60a5fa` |

### Change the font
Replace `Georgia,serif` (appears several times in the CSS) with any font you like. To use a Google Font, add a `<link>` tag inside `<head>`:
```html
<link href="https://fonts.googleapis.com/css2?family=Inter&display=swap" rel="stylesheet">
```
Then change `Georgia,serif` to `'Inter',sans-serif`.

### Change helpline numbers
Search for the phone number (Ctrl+F) — it appears in **two places**:

1. The crisis banner at the bottom of the page:
```html
<div id="mcr">🆘 iCall (India): 9152987821 &nbsp;|&nbsp; Vandrevala Foundation: 1860-2662-345</div>
```

2. Inside the first rule's response in the JavaScript:
```
iCall: 9152987821 or Vandrevala Foundation: 1860-2662-345
```

Update both with your local helpline numbers.

### Add or edit chatbot responses
All responses are inside `var rules = [...]` in the `<script>` block. Each rule looks like this:

```javascript
{
  p: [/anxious/i, /panic/i, /worried/i],   // patterns to match
  r: ["Your response here",                 // responses (one picked randomly)
      "Another response here"],
  c: ["Chip 1", "Chip 2"]                  // optional quick-reply buttons
}
```

To add a new topic, copy any rule block, change the patterns (`p`) and responses (`r`), and paste it before the last catch-all rule. The catch-all rule (`/.*/`) must always stay last.

---

## 🧠 How the Rule Engine Works

1. User sends a message
2. The engine tests the message against each rule's patterns in order
3. First match wins — a random response is picked from that rule's `r` array
4. Optional quick-reply chips appear below the bot's response
5. If the user shared their name earlier, it gets personalised into the reply

No AI, no API, no internet connection required after the page loads.

---

## 🆘 Crisis Safety

The chatbot always checks for crisis keywords first (suicide, self-harm, etc.) and responds with helpline numbers before any other rule. This check happens at the top of the rules array and cannot be bypassed by other matches.

**Always keep real, working helpline numbers** in both the banner and the crisis rule response.

---

## ⚠️ Disclaimer

MindEase is a supportive conversation tool only. It is **not** a substitute for professional mental health care, therapy, or crisis intervention. Always include accurate local helpline numbers for your target audience.

---

## 📄 License

Free to use, modify, and deploy for personal or non-commercial projects. If you use this for a commercial product, please add your own disclaimer and ensure compliance with local mental health regulations.
