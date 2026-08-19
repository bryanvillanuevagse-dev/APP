SCHOOL VALUES WORD ORDER CHALLENGE — APP PACKAGE
==================================================

This folder turns the Smart Board game into an installable "app" with its
own icon and full-screen window (no browser address bar), while staying
100% offline. It contains:

  index.html              the game itself
  manifest.json           tells the browser this is an installable app
  sw.js                   service worker — caches everything for offline use
  icon-192.png            app icon (small)
  icon-512.png            app icon (large)
  icon-512-maskable.png   app icon for Android's adaptive-icon shapes


OPTION 1 — Just run it, no install (simplest, works today)
------------------------------------------------------------
Double-click index.html. Nothing to install, works fully offline, exactly
like before. This is still the easiest option for a USB-drive workflow.


OPTION 2 — Install it as an app icon (Windows / Chromebook / Android tablet)
------------------------------------------------------------------------------
Browsers only allow "installing" a site from a real web address (http/https),
not directly from a file on a USB drive. So to get the home-screen icon and
the address-bar-free window, serve this folder locally first:

  1. Copy this whole folder onto the classroom computer.
  2. Open a terminal / command prompt in that folder.
  3. Run one of these (pick whichever is available):
       python3 -m http.server 8000
       npx serve -l 8000
  4. On the SAME computer, open Chrome/Edge and go to:
       http://localhost:8000/index.html
  5. Click the "Install" icon in the address bar (or menu > "Install app" /
     "Add to Home screen" on a tablet).
  6. The game now has its own icon and opens full-screen, like a real app.
  7. After installing once, you can stop the local server — the service
     worker has already cached everything, so it keeps working offline.

This works the same way on an Android tablet connected to the Smart Board
(open the same http://<computer's IP>:8000 address from the tablet's Chrome
browser while both devices are on the same network, then Install).


OPTION 3 — A real, signed .apk file for Android
--------------------------------------------------
A genuine .apk requires Google's Android build tools, which aren't
something that can be produced offline or from within this chat. The
practical free route, if you specifically need a distributable .apk:

  1. Host this folder somewhere with HTTPS — free options include GitHub
     Pages, Netlify, or Vercel (just upload the folder / connect the repo).
  2. Go to https://www.pwabuilder.com and enter that HTTPS URL.
  3. PWABuilder reads manifest.json (already included here) and packages
     an installable, signed Android .apk / .aab for you to download.
  4. Install that .apk on any Android tablet/board like a normal app.

Note this route needs a one-time internet connection to host the files and
run PWABuilder; the resulting installed app then runs fully offline in the
classroom, same as the browser version.


WHICH OPTION SHOULD I USE?
-----------------------------
- Smart Board driven by a Windows/Chrome-OS PC: Option 1 is genuinely
  fine — teachers just open the file. Option 2 is a nice touch if you
  want a dedicated icon and no browser chrome.
- A dedicated Android tablet/board that should feel like a real app from
  the home screen: Option 3 (actual .apk) is worth the one-time setup.
