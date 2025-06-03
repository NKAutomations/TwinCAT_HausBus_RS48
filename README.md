Hier ist eine neue README-Vorlage mit vollständigem Changelog und einer verständlichen deutschen Projektbeschreibung für dein TwinCAT_HausBus_RS485-Projekt:

---

# TwinCAT_HausBus_RS485

TwinCAT 3-basiertes Automatisierungsframework zur Ansteuerung von Haus-Bus.de-Komponenten über eine serielle RS485-Verbindung (kein Modbus).

## Projektziele

Das Projekt ermöglicht die Steuerung, Überwachung und Visualisierung verschiedener Haus-Bus.de-Komponenten (z.B. Taster- und Relaismodule) über eine eigens entwickelte, serielle RS485-Kommunikation. Ziel ist es, eine flexible, zuverlässige und erweiterbare Lösung für die Gebäudeautomatisierung zu bieten.

---

## Hauptfunktionen

- **RS485-Kommunikation:** FIFO-basiertes Master-Slave-Protokoll, speziell für Haus-Bus.de-Geräte, nicht Modbus. Zyklische Kommunikation mit mehreren Slaves (Taster, Relais, Sensoren).
- **Unterstützte Geräte:**
  - Tastermodule (z.B. 6-fach): Entprellung und Verarbeitung von Tastendrücken.
  - Relaismodule (z.B. 16-fach): Ansteuerung einzelner Relais.
  - Spezialereignisse: Temperatursensoren, Ping-Events, Reset, Broadcast etc.
- **Visualisierung:** Statusanzeigen für RS485-Master, Module und Diagnose über TwinCAT Visualisierung.
- **Erweiterbarkeit:** Neue Gerätetypen und Features können leicht ergänzt werden (eigene DUTs, Bausteine & Visualisierung).

---

## Projektstruktur

| Bereich                  | Beschreibung                                                         |
|--------------------------|----------------------------------------------------------------------|
| `POUs/RS485_Hausbus_FB/` | Funktionsbausteine für Kommunikation und Gerätesteuerung             |
| `GVLs/`                  | Globale Variablenlisten für Konfiguration, Kommunikation, Visualisierung |
| `DUTs/`                  | Benutzerdefinierte Datentypen für Ein-/Ausgänge, Events, FIFO        |
| `VISUs/`                 | Visualisierungsseiten für Diagnose und Gerätemanagement              |
| `MAIN.TcPOU`             | Hauptprogramm für zyklische Kommunikation und Logik                  |

---

## Voraussetzungen

- Beckhoff TwinCAT 3
- RS485-Schnittstelle am Steuerungssystem (z.B. über CX, IPC oder USB-Konverter)
- Haus-Bus.de-kompatible Geräte (Oder CYD, siehe https://github.com/zonfacter/ESP32_CYD_RS485_HAUS-BUS)

---

## Versionshistorie & Changelog

### V1.05 (03.06.2025)
- Überarbeitete Collision Detection im FiFo Master: Überwacht, ob bereits Datenverkehr auf dem Bus ist, bevor Befehle gesendet werden.
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.05)

### V1.04 (28.05.2025)
- Neuer Ping-Baustein, welcher überwacht, ob ein Ping kommt.
- FiFo Master kann nun alle Devices unabhängig von anderen Funktionsbausteinen anpingen.
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.04)

### V1.03 (27.05.2025)
- Neue Service-Funktionen für das Cheap Yellow Display Projekt (https://github.com/zonfacter/ESP32_CYD_RS485_HAUS-BUS).
- Manueller Modus für FiFo Master: Senden eines einzelnen Strings über Service-Visualisierung möglich.
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.03)

### V1.02 (23.05.2025)
- Implementierung des Cheap Yellow Display Projekts.
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.02)

### V1.01 (16.05.2025)
- Erstes Release des Projekts.
- [Release-Link](https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases/tag/V1.01)

Vollständiger Changelog siehe:  
- https://github.com/NKAutomations/TwinCAT_HausBus_RS485/commits/main  
- Vergleich einzelner Versionen: https://github.com/NKAutomations/TwinCAT_HausBus_RS485/releases

---

## Lizenz

Dieses Projekt ist ein Beta-Release von [NKAutomations] und ausschließlich zur internen oder Testverwendung bestimmt.

---

## Kontakt

Für Fragen oder Feedback:  
- GitHub Issues nutzen  
