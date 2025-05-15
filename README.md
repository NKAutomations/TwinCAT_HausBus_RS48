# TwinCAT_HausBus_RS48
TwinCAT RS485 Hausbus # RS485HausBus_Beta

Ein TwinCAT 3-basiertes Automatisierungsprojekt zur Ansteuerung von Haus-Bus.de-Komponenten über eine proprietäre serielle Kommunikation via RS485. Es handelt sich **nicht** um Modbus, sondern um ein eigenes, leichtgewichtiges Master-Slave-Protokoll für die Hausautomatisierung.

## Projektziel

Dieses Projekt stellt ein Framework zur Verfügung, mit dem über eine serielle RS485-Verbindung verschiedene **Haus-Bus.de-Komponenten** (z. B. Tastermodule, Relaismodule) angesteuert, überwacht und visualisiert werden können. Es dient als Ausgangsbasis für die Entwicklung individueller Hausautomatisierungslösungen.

---

## Hauptfunktionen

### 1. **RS485-Kommunikation (eigenes Protokoll)**

- Implementiert ein einfaches FIFO-basiertes Master-Slave-Protokoll.
- Kommuniziert zyklisch mit bis zu mehreren Slaves (z. B. Taster, Relais, Sensoren).
- Kein Einsatz von Modbus – die Kommunikation ist speziell auf Haus-Bus.de-Geräte zugeschnitten.

### 2. **Unterstützte Geräte**

#### Tastermodul (z. B. 6-fach)
- Verarbeitung und Entprellung von Tasterereignissen.
- Weiterleitung an Logikbausteine oder Visualisierung.
- Baustein: `fb_TasterBus6F`

#### Relaismodul (z. B. 16-fach)
- Ansteuerung einzelner Relais über Kommunikationsdaten.
- Baustein: `fb_RelaisBus16F`

#### Spezialevents
- Temperatursensoren, Ping-Events, Reset, Broadcast usw.
- Ereignisbausteine wie `fb_BusTasterEvent`, `fb_BusTempEvent`, `fb_BusBrsEvent` zur gezielten Behandlung.

---

## Projektstruktur

| Bereich | Beschreibung |
|--------|--------------|
| `POUs/RS485_Hausbus_FB/` | Alle wichtigen Funktionsbausteine für Kommunikation und Gerätesteuerung |
| `GVLs/` | Globale Variablenlisten für Konfiguration, Kommunikation und Visualisierung |
| `DUTs/` | Benutzerdefinierte Datentypen für Eingänge, Ausgänge, Events und FIFO-Kommunikation |
| `VISUs/` | Visualisierungsseiten für Diagnose und Gerätemanagement |
| `MAIN.TcPOU` | Hauptprogramm, in dem zyklisch Kommunikation und Logik verarbeitet werden |

---

## Kommunikationstechnologie

- **RS485-Interface** über TwinCAT Serial COM Bibliothek (`Tc2_SerialCom`).
- Verwendung eines FIFO-Puffers (`fb_RS485FiFoMaster`) zur Verwaltung der Nachrichten.
- Fehlerdiagnose und Verbindungsüberwachung über `fb_RS485ComCheck`.

---

## Visualisierung

Das Projekt beinhaltet Visualisierungen für:
- **RS485-Masterstatus**
- **Einzelne Taster- und Relaismodule**
- **Diagnose- und Servicezwecke**

Verwendet werden TwinCAT Visualisierungselemente in `.TcVIS`-Dateien.

---

## Erweiterbarkeit

Neue Gerätetypen oder Features können hinzugefügt werden durch:
1. Anlegen eigener DUTs für Ein-/Ausgangsdaten.
2. Erstellung eines neuen Funktionsbausteins (z. B. `fb_<NeuesGerät>`).
3. Einbindung in den Zyklus im `MAIN`.
4. Ergänzen der Visualisierung bei Bedarf.

---

## Voraussetzungen

- **Beckhoff TwinCAT 3**
- RS485-Schnittstelle am Steuerungssystem (z. B. über CX, IPC oder USB-Konverter)
- Haus-Bus.de-kompatible Geräte

---

## Lizenz

Dieses Projekt ist ein Beta-Release von [NKAutomations](https://haus-bus.de) und derzeit ausschließlich zur internen oder Testverwendung bestimmt. Lizenzbedingungen siehe `LICENSE` (falls vorhanden).

---

## Kontakt

Für Fragen oder Feedback:
- GitHub Issues nutzen oder per E-Mail an die Projektbetreuer
