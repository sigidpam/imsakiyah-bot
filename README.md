# 🕌 Imsakiyah WhatsApp Bot

<p align="center">
  <img src="assets/logo.png" alt="Imsakiyah Bot Logo" width="150"/>
</p>

A serverless, stateless WhatsApp Bot built on Google Apps Script and the Meta Cloud API. It provides hyper-accurate, localized prayer times and nearest mosque discovery worldwide without requiring user registration.

## ✨ Key Features

* **Hyper-Local Calculation Engine:** Dynamically detects the user's country and switches astronomical calculation methods on the fly (e.g., automatically applying JAKIM's 18° Subuh angle and safety margins for Malaysia, or Kemenag for Indonesia).
* **Stateless Architecture:** Bypasses API rate limits and database latency by securely passing coordinate payloads directly within WhatsApp Interactive Buttons.
* **Smart Auto-Translation (i18n):** Parses user country codes to automatically serve the UI in 9 languages (EN, ID, DE, FR, IT, ES, NL, SV, RU), with a manual `/lang` override saved to a Google Sheets database.
* **Enterprise-Grade Geocoding:** Utilizes Google's native `Maps.newGeocoder()` backend to bypass the strict rate-limiting of open-source mapping APIs.
* **Zero-Downtime Security:** Webhook is protected by custom URL query verification, and API secrets are securely stored in Google's `PropertiesService`.

## 🛠️ Tech Stack
* **Platform:** Google Apps Script (Serverless)
* **Messaging:** WhatsApp Business Cloud API (Meta)
* **Database:** Google Sheets API
* **APIs:** Aladhan API, Google Maps Reverse Geocoder

## 🚀 How It Works
1. User sends a WhatsApp Location Pin 📍
2. Bot reverse-geocodes the coordinates and presents an interactive menu.
3. User clicks **Prayer Times** or **Nearest Mosque**.
4. Bot calculates highly accurate regional times or generates a custom Google Maps radar radius link.

## 💡 Technical Highlights
*Instead of caching states in a database which slows down response times, state (lat/lon, city, country) is embedded in the `button_reply.id` payload:*
`prayer|3.1390|101.6869|Kuala Lumpur|Malaysia`

## 👨‍💻 Setup (For Developers)
1. Copy `Code.js` to a new Google Apps Script project.
2. Run `setupSecurity()` to input your Meta Tokens and Webhook secrets into `PropertiesService`.
3. Deploy as a Web App (Anyone with link).
4. Add the Web App URL to your Meta Developer Dashboard with your custom secret query parameter.
