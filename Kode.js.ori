
// Load properties globally so the rest of the script can access them securely
const ENV = PropertiesService.getScriptProperties().getProperties();

// ==========================================
// 2. EXPANDED LANGUAGE DICTIONARY (i18n)
// ==========================================
const vocab = {
  id: {
    btnPrayer: "Jadwal Salat", btnMosque: "Masjid Terdekat",
    menuText: "📍 *Lokasi Terdeteksi:*\n{city}, {country}\n\nApa yang ingin Anda cari?",
    prayerHeader: "🕌 *Waktu Salat*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Masjid Terdekat*\n\nKlik tautan di bawah ini untuk mencari masjid di radius sekitar Anda:\n\n{link}",
    instruction: "Halo *{name}*! 👋\n\nUntuk mengecek jadwal salat atau mencari masjid terdekat, silakan bagikan lokasi Anda.\n\n*Caranya:*\n1. Ketuk ikon 📎 (Attachment) atau tombol ➕\n2. Pilih *Lokasi* 📍\n3. Kirim *Lokasi Saat Ini*\n\n🌐 *Ganti Bahasa:* Ketik `/lang en`, `/lang de`, `/lang es`, `/lang id`"
  },
  en: {
    btnPrayer: "Prayer Times", btnMosque: "Nearest Mosque",
    menuText: "📍 *Location Detected:*\n{city}, {country}\n\nWhat would you like to find?",
    prayerHeader: "🕌 *Prayer Times*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Nearest Mosque*\n\nClick the link below to find mosques within your radius:\n\n{link}",
    instruction: "Hello *{name}*! 👋\n\nTo check prayer times or find the nearest mosque, please share your location.\n\n*How to do it:*\n1. Tap the 📎 (Attachment) icon or ➕ button\n2. Select *Location* 📍\n3. Send *Send your current location*\n\n🌐 *Change Language:* Type `/lang en`, `/lang de`, `/lang es`, `/lang id`"
  },
  de: {
    btnPrayer: "Gebetszeiten", btnMosque: "Nächste Moschee",
    menuText: "📍 *Standort erkannt:*\n{city}, {country}\n\nWas möchten Sie finden?",
    prayerHeader: "🕌 *Gebetszeiten*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Nächste Moschee*\n\nKlicken Sie auf den Link unten, um Moscheen in Ihrem Umkreis zu finden:\n\n{link}",
    instruction: "Hallo *{name}*! 👋\n\nUm Gebetszeiten zu überprüfen oder die nächste Moschee zu finden, teilen Sie bitte Ihren Standort.\n\n🌐 *Sprache ändern:* Tippen Sie `/lang de`, `/lang en`, `/lang id`"
  },
  fr: {
    btnPrayer: "Heures de prière", btnMosque: "Mosquée proche",
    menuText: "📍 *Position détectée :*\n{city}, {country}\n\nQue souhaitez-vous trouver ?",
    prayerHeader: "🕌 *Heures de prière*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Mosquée la plus proche*\n\nCliquez sur le lien ci-dessous pour trouver des mosquées dans votre rayon :\n\n{link}",
    instruction: "Bonjour *{name}* ! 👋\n\nPour vérifier les heures de prière, veuillez partager votre position.\n\n🌐 *Changer de langue :* Tapez `/lang fr`, `/lang en`, `/lang id`"
  },
  it: {
    btnPrayer: "Orari preghiera", btnMosque: "Moschea vicina",
    menuText: "📍 *Posizione rilevata:*\n{city}, {country}\n\nCosa vorresti trovare?",
    prayerHeader: "🕌 *Orari di preghiera*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Moschea più vicina*\n\nClicca sul link sottostante per trovare le moschee nel tuo raggio:\n\n{link}",
    instruction: "Ciao *{name}*! 👋\n\nPer controllare gli orari delle preghiere, condividi la tua posizione.\n\n🌐 *Cambia lingua:* Digita `/lang it`, `/lang en`, `/lang id`"
  },
  es: {
    btnPrayer: "Horarios de rezo", btnMosque: "Mezquita cercana",
    menuText: "📍 *Ubicación detectada:*\n{city}, {country}\n\n¿Qué te gustaría encontrar?",
    prayerHeader: "🕌 *Horarios de rezo*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Mezquita más cercana*\n\nHaz clic en el enlace a continuación para buscar mezquitas en tu radio:\n\n{link}",
    instruction: "¡Hola *{name}*! 👋\n\nPara consultar los horarios de rezo, comparte tu ubicación.\n\n🌐 *Cambiar idioma:* Escribe `/lang es`, `/lang en`, `/lang id`"
  },
  nl: { 
    btnPrayer: "Gebedstijden", btnMosque: "Nabije Moskee",
    menuText: "📍 *Locatie gedetecteerd:*\n{city}, {country}\n\nWat wil je vinden?",
    prayerHeader: "🕌 *Gebedstijden*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Dichtstbijzijnde moskee*\n\nKlik op de onderstaande link om moskeeën in je omgeving te vinden:\n\n{link}",
    instruction: "Hallo *{name}*! 👋\n\nOm gebedstijden te controleren, deel je locatie.\n\n🌐 *Taal wijzigen:* Typ `/lang nl`, `/lang en`, `/lang id`"
  },
  sv: { 
    btnPrayer: "Bönetider", btnMosque: "Närmaste Moské",
    menuText: "📍 *Plats upptäckt:*\n{city}, {country}\n\nVad vill du hitta?",
    prayerHeader: "🕌 *Bönetider*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Närmaste moské*\n\nKlicka på länken nedan för att hitta moskéer i din närhet:\n\n{link}",
    instruction: "Hej *{name}*! 👋\n\nFör att kontrollera bönetider, dela din plats.\n\n🌐 *Ändra språk:* Skriv `/lang sv`, `/lang en`, `/lang id`"
  },
  ru: { 
    btnPrayer: "Время намаза", btnMosque: "Ближайшая мечеть",
    menuText: "📍 *Местоположение:*\n{city}, {country}\n\nЧто вы хотите найти?",
    prayerHeader: "🕌 *Время намаза*\n📍 *{city}, {country}*\n📅 {date}\n\n",
    mosqueText: "🧭 *Ближайшая мечеть*\n\nНажмите на ссылку ниже, чтобы найти мечети в вашем радиусе:\n\n{link}",
    instruction: "Здравствуйте, *{name}*! 👋\n\nЧтобы узнать время намаза, пожалуйста, поделитесь своим местоположением.\n\n🌐 *Изменить язык:* Введите `/lang ru`, `/lang en`, `/lang id`"
  }
};

// ==========================================
// 3. WEBHOOK VERIFICATION
// ==========================================
function doGet(e) {
  // 🛡️ SECURITY CHECK: Ensure Meta is providing our custom password
  if (!ENV.WEBHOOK_SECRET || e.parameter.secret !== ENV.WEBHOOK_SECRET) {
    return ContentService.createTextOutput("Unauthorized");
  }

  if (e.parameter['hub.mode'] === 'subscribe' && e.parameter['hub.verify_token'] === ENV.VERIFY_TOKEN) {
    return ContentService.createTextOutput(e.parameter['hub.challenge']);
  }
  return ContentService.createTextOutput("Forbidden");
}

// ==========================================
// 4. MESSAGE HANDLING
// ==========================================
function doPost(e) {
  // 🛡️ THE FIREWALL: Drop any payload that doesn't have our URL password
  if (!ENV.WEBHOOK_SECRET || !e.parameter || e.parameter.secret !== ENV.WEBHOOK_SECRET) {
    return ContentService.createTextOutput("Unauthorized Payload");
  }

  try {
    const data = JSON.parse(e.postData.contents);
    const sheet = SpreadsheetApp.openByUrl(ENV.SHEET_URL).getSheets()[0]; 

    if (data.object === 'whatsapp_business_account') {
      const entry = data.entry[0];
      const changes = entry.changes[0].value;
      
      if (changes.messages && changes.messages[0]) {
        const message = changes.messages[0];
        const senderPhone = message.from; 
        
        const lang = getUserLang(senderPhone);
        const t = vocab[lang];
        
        let userName = "Friend"; 
        if (changes.contacts && changes.contacts[0] && changes.contacts[0].profile) {
          userName = changes.contacts[0].profile.name;
        }

        // --- SCENARIO A: TEXT COMMANDS ---
        if (message.type === 'text') {
          const textMsg = message.text.body.trim().toLowerCase();
          
          if (textMsg.startsWith("/lang ")) {
            const newLang = textMsg.split(" ")[1].substring(0, 2);
            if (vocab[newLang]) {
              setUserLang(senderPhone, newLang);
              const localizedMenu = vocab[newLang].instruction.replace("{name}", userName);
              sendMetaReply(senderPhone, `✅ OK!\n\n${localizedMenu}`);
              sheet.appendRow([new Date(), "LANG UPDATED", `User ${userName} set to ${newLang}`]);
              return ContentService.createTextOutput("Success");
            }
          }
        }
        
        // --- SCENARIO B: LOCATION SENT ---
        if (message.type === 'location') {
          const lat = message.location.latitude;
          const lon = message.location.longitude;
          const locData = getCityCountry(lat, lon);
          
          sendInteractiveMenu(senderPhone, locData.city, locData.country, lat, lon, t);
          sheet.appendRow([new Date(), "MENU SENT", `To ${userName} in ${locData.city} (Lang: ${lang})`]);
        } 
        
        // --- SCENARIO C: BUTTON CLICKED ---
        else if (message.type === 'interactive') {
          const buttonId = message.interactive.button_reply.id;
          const parts = buttonId.split('|'); 
          const action = parts[0];
          const lat = parts[1];
          const lon = parts[2];
          const city = parts[3] || "Location";
          const country = parts[4] || "";
          
          if (action === 'prayer') {
            const countryName = country.toLowerCase();
            let methodParam = ""; 
            
            if (countryName.includes("malaysia")) {
              methodParam = "&method=99&methodSettings=18,null,18&tune=1,1,0,1,1,1,0,1,0"; 
            } else if (countryName.includes("indonesia")) {
              methodParam = "&method=99&methodSettings=20,null,18"; 
            } else if (countryName.includes("singapore")) {
              methodParam = "&method=11"; 
            } else if (countryName.includes("thailand")) {
              methodParam = "&method=3"; 
            }

            const aladhanUrl = `https://api.aladhan.com/v1/timings?latitude=${lat}&longitude=${lon}${methodParam}`;
            const aladhanData = JSON.parse(UrlFetchApp.fetch(aladhanUrl).getContentText());
            const timings = aladhanData.data.timings;
            const date = aladhanData.data.date.readable;
            
            const header = t.prayerHeader.replace("{city}", city).replace("{country}", country).replace("{date}", date);
            const timesList = `Imsak: ${timings.Imsak}\nFajr/Subuh: ${timings.Fajr}\nDhuhr/Zuhur: ${timings.Dhuhr}\nAsr: ${timings.Asr}\nMaghrib: ${timings.Maghrib}\nIsha: ${timings.Isha}`;
                              
            sendMetaReply(senderPhone, header + timesList);
            sheet.appendRow([new Date(), "PRAYER SENT", `Lang: ${lang}, Math for: ${countryName || "Global Default"}`]);
          } 
          else if (action === 'mosque') {
            const mapsLink = `https://www.google.com/maps/search/masjid/@${lat},${lon},14z`;
            const replyText = t.mosqueText.replace("{link}", mapsLink);
            sendMetaReply(senderPhone, replyText);
          }
        }
        
        // --- SCENARIO D: GENERAL TEXT ---
        else if (!message.text || !message.text.body.toLowerCase().startsWith("/lang ")) {
           const instructionText = t.instruction.replace("{name}", userName);
           sendMetaReply(senderPhone, instructionText);
        }
      }
    }
    return ContentService.createTextOutput("Success");
    
  } catch (error) {
    try { 
      SpreadsheetApp.openByUrl(ENV.SHEET_URL).getSheets()[0].appendRow([new Date(), "CODE ERROR:", error.toString()]); 
      if (ENV.ADMIN_PHONE) {
        sendMetaReply(ENV.ADMIN_PHONE, `⚠️ *IMSAKIYAH BOT ERROR* ⚠️\n\nCode crashed with error:\n${error.toString()}`);
      }
    } catch(e) {}
    return ContentService.createTextOutput("Error caught");
  }
}

// ==========================================
// 5. HELPER FUNCTIONS & DATABASE LOGIC
// ==========================================

function getUserLang(phone) {
  try {
    const sheet = SpreadsheetApp.openByUrl(ENV.SHEET_URL).getSheetByName("Preferences");
    if (sheet) {
      const data = sheet.getDataRange().getValues();
      for (let i = 0; i < data.length; i++) {
        if (data[i][0].toString() === phone) return data[i][1].toString();
      }
    }
  } catch(e) {}
  
  if (phone.startsWith("62") || phone.startsWith("60") || phone.startsWith("673")) return 'id'; 
  if (phone.startsWith("49")) return 'de'; 
  if (phone.startsWith("33")) return 'fr'; 
  if (phone.startsWith("39")) return 'it'; 
  if (phone.startsWith("34")) return 'es'; 
  if (phone.startsWith("31")) return 'nl'; 
  if (phone.startsWith("46")) return 'sv'; 
  if (phone.startsWith("7")) return 'ru';  
  return 'en'; 
}

function setUserLang(phone, lang) {
  try {
    let ss = SpreadsheetApp.openByUrl(ENV.SHEET_URL);
    let sheet = ss.getSheetByName("Preferences");
    if (!sheet) {
      sheet = ss.insertSheet("Preferences"); 
      sheet.appendRow(["Phone Number", "Language"]);
    }
    const data = sheet.getDataRange().getValues();
    let found = false;
    for (let i = 0; i < data.length; i++) {
      if (data[i][0].toString() === phone) {
        sheet.getRange(i + 1, 2).setValue(lang);
        found = true;
        break;
      }
    }
    if (!found) sheet.appendRow([phone, lang]);
  } catch(e) {}
}

function getCityCountry(lat, lon) {
  try {
    const response = Maps.newGeocoder().reverseGeocode(lat, lon);
    if (response.status === 'OK' && response.results.length > 0) {
      const components = response.results[0].address_components;
      let city = "", country = "";
      for (let i = 0; i < components.length; i++) {
        const types = components[i].types;
        if (types.includes("locality") || types.includes("administrative_area_level_2")) city = components[i].long_name;
        if (types.includes("country")) country = components[i].long_name;
      }
      return { city: city || "Location", country: country };
    }
  } catch(e) {}
  
  try {
    const url = `https://nominatim.openstreetmap.org/reverse?format=json&lat=${lat}&lon=${lon}`;
    const res = UrlFetchApp.fetch(url, { muteHttpExceptions: true, headers: { "User-Agent": "ImsakiyahBot_Dev/1.0" } });
    const data = JSON.parse(res.getContentText());
    return { city: data.address.city || data.address.town || data.address.state || "Location", country: data.address.country || "" };
  } catch(e) { return { city: "Location", country: "" }; }
}

function sendInteractiveMenu(toPhone, city, country, lat, lon, t) {
  const sCity = city.replace(/\|/g, ""); const sCountry = country.replace(/\|/g, "");
  const payload = {
    messaging_product: 'whatsapp', to: toPhone, type: 'interactive',
    interactive: {
      type: 'button', body: { text: t.menuText.replace("{city}", sCity).replace("{country}", sCountry) },
      action: { buttons: [
          { type: 'reply', reply: { id: `prayer|${lat}|${lon}|${sCity}|${sCountry}`, title: t.btnPrayer } },
          { type: 'reply', reply: { id: `mosque|${lat}|${lon}|${sCity}|${sCountry}`, title: t.btnMosque } }
      ]}
    }
  };
  sendToMeta(payload);
}

function sendMetaReply(toPhone, textBody) {
  const payload = { messaging_product: 'whatsapp', to: toPhone, text: { body: textBody } };
  sendToMeta(payload);
}

function sendToMeta(payload) {
  const metaUrl = `https://graph.facebook.com/v18.0/${ENV.PHONE_NUMBER_ID}/messages`;
  UrlFetchApp.fetch(metaUrl, { method: 'post', contentType: 'application/json', headers: { 'Authorization': `Bearer ${ENV.WHATSAPP_TOKEN}` }, payload: JSON.stringify(payload), muteHttpExceptions: true });
}

