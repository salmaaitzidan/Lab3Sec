Mini-rapport

Salma AIT ZIDAN

Perimetre   : emulateur Android Studio (Pixel 6, API 33), cible testphp.vulnweb.com
Burp version: 2024.1 Community Edition
IP hote     : 192.168.1.7
Port proxy  : 8080
Date / heure: 07/06/2026 — 10h00

Preuves
  - 3 requetes capturees dans HTTP history (GET /, style.css, logo.gif)
  - Requete GET / analysee : headers complets visibles en clair

Analyse
  - Le User-Agent expose le modele exact de l'appareil (Pixel 6, Android 13)
  - Aucun cookie de session sur la page d'accueil
  - Tout le trafic transite en HTTP non chiffre : contenu lisible integralement
  - Aucun header de securite cote client observe (pas de Strict-Transport-Security)

Recommandations
  - Forcer HTTPS sur toutes les ressources, y compris les assets statiques
  - Configurer les cookies avec les attributs Secure, HttpOnly, SameSite=Strict
  - Masquer ou generaliser le User-Agent dans les applis Android en production
  - Appliquer une Network Security Configuration pour interdire le HTTP clair
