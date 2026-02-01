
# SharedMedia_Julsanity

Ein kleines LibSharedMedia-Paket mit Fonts, Texturen und Sounds für World of Warcraft AddOns.

**Inhalt**
- Fonts: Schriftarten (*.ttf)
- Sounds: Audio-Dateien (*.ogg)
- Textures: Statusbar / Background / Border Texturen (meist *.tga / *.blp oder Pfad ohne Extension)

**Kurzbeschreibung**
Dieses AddOn registriert verschiedene Medientypen bei `LibSharedMedia-3.0`, sodass andere AddOns diese Medien per `LSM:Fetch` verwenden können.

Beispiel-Code aus diesem Projekt (vereinfacht):

```lua
local LSM = LibStub("LibSharedMedia-3.0")

-- Schriftart registrieren
LSM:Register("font", "Accidental Presidency", "Interface\\AddOns\\SharedMedia_Julsanity\\Fonts\\Accidental_Presidency.ttf")

-- Sound registrieren
LSM:Register("sound", "1 -Naowh", "Interface\\AddOns\\SharedMedia_Julsanity\\Sounds\\1 -Naowh.ogg")

-- Statusbar / Textur registrieren
LSM:Register("statusbar", "Shield", [[Interface\\AddOns\\SharedMedia_Julsanity\\Textures\\Shield]])

-- Background / Border
LSM:Register("background", "MyBackground", "Interface\\AddOns\\SharedMedia_Julsanity\\Textures\\Background.tga")
LSM:Register("border", "MyBorder", "Interface\\AddOns\\SharedMedia_Julsanity\\Textures\\Border.tga")
```

Hinweis: In WoW-Lua-Strings werden Backslashes oft escaped, daher doppelte Backslashes (`\\`) oder Lua-Longstrings (`[[...]]`) verwenden.

Unterstützte Medientypen (häufig verwendet mit LibSharedMedia):
- `font` — TrueType-Schriftarten (.ttf)
- `sound` — Audiodateien (.ogg)
- `statusbar` — Texturen für Statusleisten
- `background` — Hintergrundtexturen
- `border` — Rahmen-/Border-Texturen

Wie AddOns die Medien verwenden:
- `local font = LSM:Fetch("font", "Name")` — gibt Pfad bzw. Asset zurück
- `local sound = LSM:Fetch("sound", "Name")` — Pfad zur Sounddatei
- `LSM:List("font")` — liefert alle registrierten Fonts

Best Practices
- Eindeutige Namen wählen (ggf. mit Prefix), damit andere AddOns keine Namenskollisionen haben.
- Pfade im TOC eintragen: Stelle sicher, dass alle Fonts/Sounds/Textures in der `.toc`-Datei gelistet sind, damit sie in das AddOn gepackt werden.
- Dateiformate: Fonts `.ttf`, Sounds `.ogg`, Texturen `.tga`/`.blp` (oder Pfad ohne Extension wie in manchen Projekten).

Fehlerbehebung
- Wenn registrierte Medien nicht auftauchen: Prüfe, ob `LibSharedMedia-3.0` vorhanden und die richtige Version ist.
- Achte auf korrekte Pfade in `LSM:Register` und dass die Dateien in der AddOn-Ordnerstruktur vorhanden sind.

Lizenz
Dieses Repository enthält eine benutzerdefinierte Lizenzdatei (`LICENSE`) mit Nutzungsbedingungen — siehe [LICENSE](LICENSE) für Details.


