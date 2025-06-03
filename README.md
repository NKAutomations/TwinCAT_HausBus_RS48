# TwinCAT_HausBus_RS485

Ein modulares TwinCAT 3-Framework zur komfortablen Ansteuerung, Überwachung und Visualisierung von Haus-Bus.de-Komponenten über eine serielle RS485-Verbindung – **ohne Modbus**, sondern mit maßgeschneidertem Protokoll.

---

## 🚀 Projektziele

Dieses Projekt hat das Ziel, die Integration und Automatisierung von Haus-Bus.de-Komponenten in Beckhoff TwinCAT 3 so einfach, robust und erweiterbar wie möglich zu gestalten.  
Es ermöglicht eine **zyklische, kollisionssichere Kommunikation** mit diversen Modulen (z. B. Taster, Relais, Sensoren) und bietet umfassende Diagnose- und Visualisierungsfunktionen – ideal für professionelle Gebäudeautomation und ambitionierte Eigenbauprojekte.

---

## 🛠️ Hauptfunktionen

- **FIFO-basierte, kollisionssichere RS485-Kommunikation**  
  - Eigenes Master-Slave-Protokoll (kein Modbus!) speziell für Haus-Bus.de und CYD-Komponenten  
  - **Kollisionsüberwachung:** Der Master prüft vor jedem Sendevorgang, ob der Bus frei ist → verhindert Datenverluste und Störungen  
  - **Individuelle Adressierung** und Verwaltung mehrerer Slaves (Taster, Relais, Sensoren, Displays)  
  - **Telegrammwarteschlange:** FIFO-Queue für ausgehende und eingehende Nachrichten

- **Gerätespezifische Bausteine & Events**  
  - **Tastermodule:** Komfortable Entprellung, differenzierte Erkennung (kurz/lang, mehrfach), Statusweitergabe  
  - **Relaismodule:** Ansteuerung einzelner Kanäle, Rückmeldung über aktuelle Zustände  
  - **Sonderfunktionen:** Temperatursensoren, Ping/Alive-Events, Resets, Broadcasts u.v.m.  
  - **Ping-Baustein:** Überwacht zyklisch die Erreichbarkeit aller Devices, meldet Ausfälle an die Visualisierung  
  - **Service-Modus:** Einzelne Telegramme können manuell verschickt und empfangen werden (z. B. für Debugging/Tests)

- **Moderne Visualisierung (HMI)**  
  - **Statusanzeigen:** Übersichtliche Darstellung von Busverkehr, Fehlerzähler, Telegrammstatistiken, Zeitüberschreitungen  
  - **Live-Diagnose:** Anzeige aller bekannten Geräte, Status- und Fehlerdiagnose in Echtzeit  
  - **Direkte Bedienung:** Relais schalten, Taster simulieren, Geräte manuell testen  
  - **Servicepanel:** Spezialansicht zum gezielten Senden/Empfangen von Rohdaten und Analyse des Busverkehrs

- **Maximale Erweiterbarkeit & Wartbarkeit**  
  - **Modulares Design:** Neue Gerätetypen, Protokollerweiterungen oder Visuals lassen sich einfach ergänzen  
  - **Klare Trennung:** Kommunikation, Logik, Visualisierung und Konfiguration sind sauber getrennt  
  - **Dokumentation & Kommentare:** Ausführliche Hilfetexte und durchdachte Benennung erleichtern Wartung und Weiterentwicklung

---

## 🗂️ Projektstruktur

| Verzeichnis/Datei             | Zweck/Erklärung                                                                                       |
|-------------------------------|------------------------------------------------------------------------------------------------------|
| `POUs/RS485_Hausbus_FB/`      | **Funktionsbausteine** für Kommunikationslogik, Master/Slave-Verwaltung, Gerätemanagement            |
| `GVLs/`                       | **Globale Variablenlisten** für Konfiguration, Kommunikationsstatus, Visualisierung                  |
| `DUTs/`                       | **Custom Datentypen** für Ein-/Ausgänge, Telegrammstruktur, Events, FIFO-Queues                      |
| `VISUs/`                      | **Visualisierungsseiten**: Übersicht, Geräteverwaltung, Live-Diagnose, Service/Manuellsteuerung      |
| `MAIN.TcPOU`                  | **Hauptprogramm** zur zyklischen Busansteuerung und Steuerlogik                                      |

---

## ⚡ Voraussetzungen

- **Beckhoff TwinCAT 3** (XAE + Runtime)
- **RS485-Schnittstelle** am Zielsystem (z. B. Beckhoff CX, IPC, USB-RS485-Wandler)
- **Kompatible Haus-Bus.de- oder CYD-Geräte**  
  → Alternativ: [ESP32_CYD_RS485_HAUS-BUS](https://github.com/zonfacter/ESP32_CYD_RS485_HAUS-BUS)  

---

## 📝 Versionshistorie & Changelog

### V1.06 (03.06.2025)
- **Neue Versionslogik:** Umstellung auf Major.Minor.Patch, ausführliche Changelogs ab dieser Version.
- **Dokumentation & Visuals überarbeitet:** README und Visualisierung modernisiert, zusätzliche Diagnose- und Hilfetexte.
- **Kommunikations- & Fehlerhandling verbessert:** Noch robuster gegen Busfehler und Timeouts.
- **Bausteinbeschreibungen erweitert:** Alle Hauptbausteine nun mit erklärenden Kommentaren.
- **Release-Link:** [V1.06 Release](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.06)

### V1.05 (03.06.2025)
- Überarbeitete Collision Detection im FiFo Master (Busverkehrsprüfung vor jedem Senden)
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.05)

### V1.04 (28.05.2025)
- Neuer Ping-Baustein, überwacht zyklisch Geräteverfügbarkeit, meldet Ausfälle
- FiFo Master kann unabhängig alle Devices anpingen
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.04)

### V1.03 (27.05.2025)
- Servicefunktionen für das Cheap Yellow Display (Projekt: [ESP32_CYD_RS485_HAUS-BUS](https://github.com/zonfacter/ESP32_CYD_RS485_HAUS-BUS))
- Manueller Modus: Senden einzelner Strings über die Visualisierung möglich
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.03)

### V1.02 (23.05.2025)
- Integration des Cheap Yellow Display Projekts
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.02)

### V1.01 (16.05.2025)
- Erstes Release
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.01)

**Vollständige Änderungshistorie:**  
- [Alle Commits](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/commits/main)  
- [Release-Vergleiche](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases)

---

## 🧩 Detaillierte Bausteinerläuterung

**RS485_Hausbus_FB_Master**  
> *Der zentrale Steuerbaustein des Systems.*  
> - Steuert den gesamten Telegrammfluss zwischen Master und Slaves
> - Prüft Busverfügbarkeit (Collision Detection)
> - Verarbeitet FIFO-Warteschlangen
> - Überwacht Pings, Fehler, Timeouts  
> - Meldet Kommunikationsprobleme an Visualisierung & Logik

**VISU_Hausbus_Main / Service / Diagnose**  
> - Übersichtliches HMI für Überwachung, Bedienung, Service
> - Live-Ansichten für schnellen Systemstatus
> - Direkte Interaktion mit Geräten (Schalten, Simulieren, Testen)

---

## 📄 Lizenz

Dieses Projekt befindet sich im Beta-Stadium und ist ausschließlich für interne Zwecke oder Testeinsätze im Rahmen von [NKAutomations] freigegeben.

---

## 💬 Kontakt

**Fragen, Wünsche oder Bugreports?**  
→ Bitte das [GitHub-Issue-Board](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/issues) nutzen!

---

**Viel Spaß beim Automatisieren!**
