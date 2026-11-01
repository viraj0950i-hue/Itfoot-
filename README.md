8# Itfoot

Android ke liye ek React Native (Expo) app, do core features ke saath:

1. **Voice Assistant** – mic dabakar boliye, app aapse Hindi/Hinglish mein
   baat karta hai (abhi offline, rule-based replies — samay, taarikh,
   greetings, safety madad).
2. **Family Safety** – SOS button jo saved emergency contacts ko aapki live
   location ke saath SMS bhejta hai, aur **sirf aapki saaf sahmati** ke baad
   chalu hone wali live location sharing.

## Design principle: consent-first, never covert

Yeh app jaan-boojh kar kisi aur ke phone ka chhupa hua ya door se control
nahi deta. Location sharing:

- hamesha us hi phone par, us hi vyakti dwara chalu ki jaati hai jiska
  data share ho raha hai (Consent screen),
- screen par ek saaf indicator deti hai jab sharing ON hoti hai,
- kabhi bhi usi vyakti dwara band ki ja sakti hai.

Agar aapko iske alawa kuch chahiye (jaise doosre vyakti ke phone ko bina
unki jaankari ke control karna), Itfoot use support nahin karta — aisa
software stalkerware ban jaata hai, jo kai jagah illegal hai aur bhaari
privacy/safety risk banata ha7i.

## Project layout

## Setup (apne computer/Mac/Windows par)

```bash
npm install
npx expo start

npx expo prebuild
npx expo run:android
Paste karne ke baad neeche scroll karke **"Commit changes"** (green button) dabayein. Ye hua **File 12/12** — ab tak jo bhi files ho chuki hain, baaki bachi hui files ke liye wahi `github.com/viraj0950i-hue/Itfoot-/new/main` URL dubara use karein.
{
  "name": "itfoot",
  "version": "1.0.0",
  "main": "node_modules/expo/AppEntry.js",
  "private": true,
  "scripts": {
    "start": "expo start",
    "android": "expo start --android",
    "ios": "expo start --ios",
    "web": "expo start --web"
  },
  "dependencies": {
    "expo": "~51.0.0",
    "expo-status-bar": "~1.12.1",
    "expo-speech": "~12.0.2",
    "expo-location": "~17.0.1",
    "expo-sms": "~12.0.1",
    "expo-haptics": "~13.0.1",
    "react": "18.2.0",
    "react-native": "0.74.5",
    "@react-navigation/native": "^6.1.17",
    "@react-navigation/native-stack": "^6.9.26",
    "react-native-screens": "~3.31.1",
    "react-native-safe-area-context": "4.10.5",
    "@react-native-async-storage/async-storage": "1.23.1",
    "@react-native-voice/voice": "^3.2.4"
  },
  "devDependencies": {
    "@babel/core": "^7.24.0"
  }
}
