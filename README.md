# ATOLL — Landing Page

Marketing-Landingpage für **ATOLL — The Scuba OS**, das Betriebssystem für PADI-Tauchschulen.

🔗 Live: https://www.atoll-os.com (nach DNS-Setup, siehe unten)
📦 Repo: https://github.com/scubanet/atoll-os.com

## Struktur

```
.
├── index.html      # Gesamte Seite — HTML/CSS/JS in einer Datei
├── screens/        # Produkt-Screenshots aus Atoll (Cockpit, Calendar, Courses, Skills, Pool)
└── CNAME           # Custom-Domain-Konfiguration für GitHub Pages (www.atoll-os.com)
```

Keine Build-Schritte, kein Framework, kein Node nötig. Reines statisches HTML.

## Lokal ansehen

Einfach `index.html` im Browser öffnen, oder mit einem simplen lokalen Server:

```bash
python3 -m http.server 8000
# dann: http://localhost:8000
```

## Deployment via GitHub Pages

1. Im Repo unter **Settings → Pages**
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` / Ordner `/ (root)`
4. Speichern — nach 1–2 Minuten ist die Seite live unter `https://scubanet.github.io/atoll-os.com/`

## Custom Domain: www.atoll-os.com

Die `CNAME`-Datei im Repo ist bereits auf `www.atoll-os.com` gesetzt. Damit das greift:

### DNS bei Infomaniak setzen (Domain liegt bei Infomaniak)

1. Im [Infomaniak Manager](https://manager.infomaniak.com) einloggen
2. Auf **atoll-os.com** klicken
3. Im linken Menü **DNS-Zone**
4. **Eintrag hinzufügen** → Typ **CNAME**
5. Eingeben:
   - Quelle/Source: `www`
   - Ziel: `scubanet.github.io`
   - TTL: Standard
6. Speichern — Propagation laut Infomaniak bis zu 48h, meist deutlich schneller

**Nackte Domain (`atoll-os.com` ohne www):** Infomaniak erlaubt keinen CNAME direkt auf der Root-Domain. Stattdessen die **Web-Weiterleitung**-Funktion auf Root-Ebene der Domain-Verwaltung nutzen (nicht in der DNS-Zone) und auf `www.atoll-os.com` weiterleiten lassen.

### Danach bei GitHub

1. Repo pushen (CNAME-Datei ist schon enthalten)
2. **Settings → Pages**: Custom domain sollte automatisch `www.atoll-os.com` zeigen (aus der CNAME-Datei gelesen)
3. Warten auf grünes Häkchen bei der DNS-Prüfung
4. **„Enforce HTTPS"** aktivieren, sobald verfügbar (GitHub stellt automatisch ein Zertifikat aus)

## Bearbeiten

Die ganze Seite lebt in `index.html` — Texte sind über `data-de` / `data-en` Attribute zweisprachig (DE/EN-Toggle oben rechts). Beim Ändern von Texten immer beide Sprachversionen pflegen.

