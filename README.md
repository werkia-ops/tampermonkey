# Werkia Tampermonkey Toolboxes

Fertig gebaute Tampermonkey-Userscripts fuer KAM/CEM/OBC. Dieses Repo wird automatisch von der internen Werkia_OPS-CI gepflegt (`.github/workflows/mirror-toolboxes.yml`) - Aenderungen hier werden beim naechsten Sync ueberschrieben.

Installation: die gewuenschte `.user.js`-Datei unten anklicken - Tampermonkey erkennt sie automatisch und bietet die Installation an. Updates kommen danach automatisch ueber Tampermonkeys eigene Update-Pruefung (`@updateURL`), ohne dass hier nochmal etwas angeklickt werden muss.

## KAM Toolbox

[KAM-Toolbox.user.js](https://raw.githubusercontent.com/willywerkia/tampermonkey/main/KAM-Toolbox.user.js)

Enthaltene Funktionen:

- Prueft alle 5 Minuten, ob eine neuere Version der Toolbox veroeffentlicht ist, und bietet dann in einem kleinen Hinweis unten rechts Aktualisieren und Neu laden an. "Spaeter" blendet den Hinweis fuer vier Stunden aus.
- Kleine ?-Knoepfe an Dialogen, Leisten und Panels erklaeren die jeweilige Funktion. Der Hilfe-Knopf unten links und der Tampermonkey-Menueeintrag oeffnen eine Uebersicht aller Funktionen mit Kennzeichnung, ob sie nur anzeigen oder Daten aendern.
- Setzt Wiedervorlagedatum und KAM-Status fuer die angehakten Zeilen der Matches-Liste gleichzeitig (Haken-Liste nach Arbeitgeber gruppiert). Bei Out werden offene Terminvorschlaege abgelehnt. "Alle weiterleiten" leitet alle Terminvorschlaege mit Status Vorschlag der angehakten Matches weiter. "Vergangene ablehnen" lehnt Terminvorschlaege mit Status Vorschlag ab, deren Termine alle in der Vergangenheit liegen.
- In der Tags-Ansicht von Meine Matches (Knopf „TAGS“) wird KAM WVL zum Datumsfeld wie in der normalen Liste: ein neues Datum speichert sofort, leeren entfernt die WVL. Beim Schließen der Ansicht lädt die Liste neu.
- Neben dem Knopf „TAGS“ in Meine Matches ein zweiter Knopf „Tags in HC/HHC“: zählt die Matches mit ungelesenem Tag für dich, deren KAM-Status Hot Case oder Hot Hot Case ist (alle 2 Minuten und bei jeder Änderung am TAGS-Zähler neu). Ein Klick öffnet die Tags-Ansicht nur mit diesen Matches; der normale Knopf „TAGS“ zeigt weiter alle.
- Zeigt bei jedem Arbeitgeber ein Badge zur Kontakthaeufigkeit (z. B. "Direkter Kontakt", "Kein Kontakt") und einen Vorschlag aus den VT-Zahlen der letzten 4 Wochen.
- Ganz oben im Matchkommentar-Dialog der Hauptansprechpartner des Arbeitgebers mit Name, Telefonnummer und E-Mail, je mit Kopierknopf, dazu "Alles kopieren". Ohne markierten Haupt-AP steht der erste, mit Hinweis.
- AG-Notizen mit Tags (Matches, AP, Vakanzen, Prozess) als Arbeitgeberkommentar. Oben im Matchkommentar-Dialog, unter dem Ansprechpartner, stehen die letzten Notizen mit Tag Matches, daneben speichert "Als AG-Notiz speichern" den Text aus dem Kommentarfeld mit den gewählten Tags am Arbeitgeber statt am Match. In Meine Matches zeigen Chips hinter der AG Response Rate die Notizen mit Tag AP und Prozess, das Vakanz-Panel die mit Tag Vakanzen.
- Im Matchkommentar-Dialog an Stelle der Spalte "AG Fragebogen" der OM-Fragebogen des Matches, nur lesend: Anforderungen der Vakanz neben den Angaben des Kandidaten (Position, Berufserfahrung, Deutschkenntnisse, Führerschein, Auto, Reise-/Montagebereitschaft, Gehalt, Fachbereiche, Stellenumfang, Anerkennung, Entfernung) mit Bewertung passt/prüfen/passt nicht, darunter "Zusätzliche Information - OM". Der Haken "AG-Fragebogen anzeigen" blendet die native Spalte für diesen Dialog wieder ein.
- Zeigt in Meine Matches unter dem KAM Status den CEM Status und die zustaendige CEM-Person. Ein Klick auf den Namen kopiert ihn.
- Steht ein Match in Meine Matches auf Out, steht klein unter der CEM-Zeile der CEM-Out-Grund, z. B. "CEM-Out: BEW nicht responsive". Bei OM "Nicht senden" steht dort dessen Grund ("OM-Out: Doppelt"). Den eigenen KAM-Out-Grund zeigt sie nicht. Ohne hinterlegten Grund "ohne Grund", Absagen aus der Kandidaten-App als "Absage in der App: ...".
- Technische Hintergrundfunktion ohne eigene Anzeige - merkt sich Kandidat/Vakanz des offenen Fragebogens fuer andere Funktionen.
- Blendet neben dem OM-Fragebogen ein Panel mit den oeffentlichen Vakanzangaben ein ("Zustaendigkeiten", "Dein Profil").
- Vergleicht Fragebogen-Antworten mit den Vakanzanforderungen und zeigt eine farbige Ampel-Empfehlung plus Notizfeld.
- Berechnet und zeigt die Fahrstrecke/-zeit zwischen Kandidatenwohnort und Arbeitsort im Fragebogen.
- Oeffnet die Kandidatendatei per Klick direkt in einem Popup statt in einem neuen Tab.
- Zeigt eine Konfetti-/Feier-Animation, wenn ein Match auf "Senden" oder "Hired" gesetzt wird.
- Zeigt im Chat ein farbiges Banner mit dem aktuellen CEM/KAM-Status des zugehoerigen Matches.
- Korrigiert den Chat-Button in "Meine Matches", damit er direkt die richtige Unterhaltung oeffnet.
- Kopiert Terminvorschlaege (Ort, Hinweise, Datum/Uhrzeit) per Knopfdruck von einem Dialog in einen anderen.
- Haken "Prio" im Terminvorschlag-Dialog: schreibt #prio in die Notizen des Termins, die VT Automatik postet VTA/VTV/VTS des Matches dann mit :alert11:.
- Zwei Knoepfe im VTA/VTV-Block der Terminspalte in Meine Matches (ohne Termin dort allein): "Dringend" markiert die Vakanz ueber den Slack-Bot der dringenden Vakanzen und zeigt den aktuellen Zustand, "Push" postet eine Push Request in #push-requests.
- Knopf „An CEM“ je Match in Meine Matches: schickt der CEM-Person des Kandidaten (und ihrer Vertretung) über den OPS-Bot eine Slack-DM mit Kandidat, Vakanz, Match-Link und optionalem Kommentar, unter deinem Namen. Der Dialog zeigt vorher, wer sie bekommt.
- Liest den Betreff einer geoeffneten Outlook-Bewerbungsmail, findet den passenden Match per GraphQL und setzt KAM Status auf "Out" inkl. Pflichtgrund - offene Terminvorschlaege werden ebenfalls abgelehnt.
- Ueberdeckt in der Vakanzliste die Statusspalte mit einem Dropdown, das den Vakanz-Status direkt speichert. "Alle ändern" im Spaltenkopf setzt den Status fuer die angehakten sichtbaren Vakanzen gemeinsam.
- Kleine Marke „Gecrawlt“ hinter dem Vakanztitel in der Vakanzliste und in Meine Matches, wenn die Stelle aus dem Auto-Crawling kommt; Tooltip „Gecrawlt am …“. Andere Vakanzen bekommen keine Marke. Daten aus dem n8n-Workflow Crawling Herkunft (alle 30 Minuten aus Airtable).
- Fuegt im Arbeitgeberprofil OM-Flag-Vorlagen direkt am Feld OM Notes ein.
- Markiert dringend zu besetzende Vakanzen bei potenziellen Kandidaten-Matches farblich in der Liste.
- Knopf "Vertretungen" neben den Filter-Knöpfen von Meine Matches und im Tampermonkey-Menü: trägt Vertretungen ein, die VT Automatik, VT Bot und VT-Status-Hinweis zusätzlich taggen. Gespeichert im n8n-Workflow Vertretungen.
- Knopf „Heute“ in Meine Matches: Seitenleiste mit bestätigten Terminen, heute fälligen WVL, eigenen Remindern und Team-Einträgen der Leitung. Glocke je Match-Zeile setzt einen Reminder (Zeit + Text). Auf jeder Adminpanel-Seite erinnert ein Popup an fällige Reminder, Termine in 15 Minuten und die WVL des Tages. Reminder und Team-Einträge liegen im n8n-Workflow Toolbox-Daten.
- Dropdown ueber der Liste mit gespeicherten Filterkombinationen. "Aktuellen Filter speichern" uebernimmt Filter, Sortierung und Seitengroesse der Ansicht; Vorlagen liegen lokal im Browser und ueberstehen Toolbox-Updates.
- Leiste ueber dem Editor im Matchkommentar-Dialog: Kuerzel-Knoepfe (tne, VTA, AV ...) fuegen den ausgeschriebenen Text in den Matchkommentar ein, eine AG-Notiz legt keiner an. Beim Tippen eines Kuerzels schlaegt ein Popup den Text vor, Tab uebernimmt. Reiter "Vorlagen" fuer eigene lange Texte, pro Person in den Toolbox-Daten gespeichert. Am Match aendert sich nichts.
- Knopf „@CEM“ in der Werkzeugleiste des Matchkommentar-Dialogs: erwähnt die CEM-Person des Kandidaten am Cursor. Rechtsklick öffnet die Auswahl aller CEM-Personen mit Suchfeld. Abgeschickt wird wie immer mit dem Pfeil.
- Focus-Modes in Meine Matches neben den Filtervorlagen: ein Klick setzt Filter, Sortierung und eine hervorgehobene Spalte. Fester Modus "VTA-Session" zeigt die VT-Anfragen mit der Terminspalte vorn. Eigene Modi lassen sich aus dem aktuellen Filter speichern, "Verlassen" stellt die vorige Ansicht wieder her.
- Erwähnt man im Kommentar-Editor jemanden, der heute vertreten wird, kommt die Vertretung als zweite Erwähnung direkt dahinter. Wer sie wieder löscht, bekommt sie nicht erneut. Ohne Toolbox taggt der n8n-Workflow Vertretungen Erwähnungen per Folgekommentar nach.
- In Outlook Web: zur geöffneten Mail eines Arbeitgebers der Vorschlag aus dem n8n-Workflow KAM Mail Assistent (Status, Grund, Kommentar mit CEM-Erwähnung, WVL, AG-Notiz). Blauer Knopf unten rechts, jede Aktion einzeln abwählbar, „Übernehmen“ schreibt mit der eigenen Anmeldung.
- Prio-Liste in Meine Matches: Knopf "Prio-Liste" oben rechts klappt ein Panel mit den heute markierten Arbeitgebern auf. Markieren per Stern vor dem Arbeitgeber oder im Panel, abhaken, Notiz bearbeiten. Um 17:30 ein Fenster zum Tagesabschluss, Offenes wandert auf den nächsten Arbeitstag. Schalter "Prio zuerst" sortiert die Zeilen der Seite. Gespeichert pro Person über Toolbox-Daten, lesbar für die heutige Vertretung.
- Knopf „AG-Pause“ in Meine Matches und „Pausieren“ in der Leiste des Arbeitgebers: pausiert einen Arbeitgeber (Standort pausiert) samt veröffentlichter Stellen bis zu einem Datum. Am Morgen von „Wieder aktiv ab“ setzt der n8n-Workflow Arbeitgeber Pause beides zurück, pausierende Person und KAM bekommen eine Slack-DM. Verlängern und vorzeitig beenden im selben Dialog.
- Feste VTA-Notiz je Arbeitgeber (z. B. Buchungslink): Box unter dem Notizfeld im Terminvorschlag-Dialog, bei neuen Terminen einmal ans Notizfeld angehängt. Pflege über Knopf „VTA-Notiz“ am Arbeitgeber, direkt in der Box oder im Tampermonkey-Menü. Gespeichert im n8n-Workflow VTA Notizen.
- Knopf „Mail an AP“ im Matchkommentar-Dialog öffnet den AP-Dialog „Email senden“ desselben Matches. Leiste im Mail-Dialog fügt die Namen aller offenen Bewerbungen beim Arbeitgeber ein (ohne 20er-Grenze), „Offene Bewerber“ zeigt und kopiert die vollständige Liste.

## CEM Toolbox

[CEM-Toolbox.user.js](https://raw.githubusercontent.com/willywerkia/tampermonkey/main/CEM-Toolbox.user.js)

Enthaltene Funktionen:

- Umrandet das Startdatum im Kandidatenfragebogen. Bei leerem oder vergangenem Datum erscheint oben ein roter Hinweis. Direkt am Feld steht klein und grau, wann das Startdatum zuletzt geändert wurde, aus der Versionshistorie des Kandidaten.
- Prueft alle 5 Minuten, ob eine neuere Version der Toolbox veroeffentlicht ist, und bietet dann in einem kleinen Hinweis unten rechts Aktualisieren und Neu laden an. "Spaeter" blendet den Hinweis fuer vier Stunden aus.
- Kleine ?-Knoepfe an Dialogen, Leisten und Panels erklaeren die jeweilige Funktion. Der Hilfe-Knopf unten links und der Tampermonkey-Menueeintrag oeffnen eine Uebersicht aller Funktionen mit Kennzeichnung, ob sie nur anzeigen oder Daten aendern.
- Setzt in CEM Meine Matches CEM WVL und CEM Status fuer die angehakten sichtbaren Matches gleichzeitig (Haken-Liste nach Arbeitgeber gruppiert, in Meine Kandidaten die Matches aller aufgeklappten Kandidaten). Bei Hired und Out wird die CEM WVL geleert, Out braucht einen Grund und lehnt offene Terminvorschlaege ab. "Alle weiterleiten" leitet alle Terminvorschlaege mit Status Vorschlag der angehakten Matches weiter. "Vergangene ablehnen" lehnt Terminvorschlaege mit Status Vorschlag ab, deren Termine alle in der Vergangenheit liegen.
- Setzt in CEM Meine Kandidaten Kandidat-Status und Kandidat-WVL fuer mehrere sichtbare Kandidaten gleichzeitig. Der Dialog listet alle Kandidaten der aktuellen Seite zum An- und Abhaken.
- Zeigt bei jedem Arbeitgeber ein Badge zur Rueckmeldegeschwindigkeit (z. B. "Schnelle Rueckmeldung", "Keine Rueckmeldung").
- Markiert Vorschlaege, wenn beim Arbeitgeber bereits ein Match auf den Status "Senden" gestellt wurde. Bis 90 Tage bleibt die Zeile rot gefuellt, danach nur rot umrandet. Der Hinweis zeigt den Zeitpunkt der Statusaenderung und bei derselben Vakanz den KAM-Status.
- Markiert Zeilen von Arbeitgebern mit besonderer Absprache (GA-TEC) farblich mit Hinweistext "[Absprache vor OFM]".
- Technische Hintergrundfunktion ohne eigene Anzeige - merkt sich den Kontext des offenen Fragebogens fuer andere Funktionen.
- Blendet neben dem Fragebogen ein Panel mit den oeffentlichen Vakanzangaben ein.
- Faerbt das Status-Auswahlfeld eines Matches passend zum gewaehlten Status ein (z. B. Hot Case orange, Hired gruen).
- Vergleicht Fragebogen-Antworten mit den Vakanzanforderungen und zeigt eine farbige Match-Empfehlung an.
- Berechnet beim offenen Fragebogen Fahrzeit und Strecke zwischen Kandidatenwohnort und Arbeitsort, zeigt die Vakanzart und bei ortsgebundenen Vakanzen ab 50 Min einen Totenkopf.
- Zeigt auf Potenzielle Matches in jeder Zeile die Fahrzeit vom Kandidatenwohnort zur Vakanz und die Vakanzart (Start von Zuhause, Landes-/bundesweit, Montage). Ortsgebundene Vakanzen ab 50 Min Fahrzeit bekommen einen Totenkopf. Hat der Kandidat mehrere Adressen, zaehlt die schnellste Route (wie im Fragebogen). Die Routen laden nacheinander im Hintergrund und bleiben eine Woche im Browser gespeichert.
- Schreibt in CEM › Meine Matches und Meine Kandidaten hinter jeden Termin die Herkunft (AG = Termine vom Arbeitgeber, Kand. = vom Kandidaten) und umrandet offene Termine vom Arbeitgeber. Auf KAM-Seiten aus.
- Ergaenzt die Kandidatenliste einer Vakanz um Zusatzinfos je Kandidat (Reisebereitschaft, Status, Registrierungsdatum, Telefonnummer) und eine Anruf-Empfehlung.
- Erlaubt auf Potenzielle Matches die Auswahl mehrerer Arbeitgeber und vorhandener Jobs für ein gemeinsames Offline-Match-Formular. Bei einem Arbeitgeber mit vorhandenem Match ist vor dem Öffnen eine Bestätigung nötig; Terminvorschläge lassen sich gesammelt löschen.
- Markiert dringend zu besetzende Vakanzen bei potenziellen Kandidaten-Matches farblich in der Liste.
- Knopf "Vertretungen" neben den Filter-Knöpfen von Meine Kandidaten und im Tampermonkey-Menü: trägt Vertretungen ein, die VT Automatik, VT Bot und VT-Status-Hinweis zusätzlich taggen. Gespeichert im n8n-Workflow Vertretungen.
- Markiert auf Potenzielle Matches Arbeitgeber von der VTA-Sperrliste rot mit dem Label "Keine CEM-VTA". Knopf "VTA-Sperrliste" neben Vertretungen in Meine Kandidaten und im Tampermonkey-Menü: Arbeitgeber per Name oder ID suchen, eintragen und austragen. Gespeichert im n8n-Workflow CEM VTA Sperre.
- Ampel vor jedem Kandidatennamen in Meine Kandidaten: Grün (Hot Case, bestätigter VT, offener KAM-VTA oder die ersten 7 Werktage nach der Zuteilung), Gelb (nichts davon, Matches noch offen), Rot (inaktiv, alle Matches out oder 7 Werktage ohne Kontakt). Der Grund steht im Tooltip, ein Klick setzt die Farbe von Hand. Dickes NEW hinter dem Namen, solange du seit der Zuteilung keinen Kontakt hattest. Die Knöpfe Grün/Gelb/Rot und „Nur NEW“ filtern die Liste über alle Seiten. Gerechnet im n8n-Workflow CEM Ampel.
- Dropdown ueber der Liste mit gespeicherten Filterkombinationen. "Aktuellen Filter speichern" uebernimmt Filter, Sortierung und Seitengroesse der Ansicht; Vorlagen liegen lokal im Browser und ueberstehen Toolbox-Updates.
- Warnt auf Potenzielle Matches, wenn ein vorgeschlagener Arbeitgeber bei diesem Kandidaten als No-Go hinterlegt ist - rot bei demselben Arbeitgeberprofil oder derselben Firmengruppe (gleicher Webauftritt), gelb bei einem blossen Namenstreffer, der noch geprueft werden muss.
- Haken "Prio" im Terminvorschlag-Dialog: schreibt #prio in die Notizen des Termins, die VT Automatik postet VTA/VTV/VTS des Matches dann mit :alert11:.
- Knopf "WA" in Meine Matches und Meine Kandidaten: fuellt eine WhatsApp-Vorlage mit Kandidaten- und Matchdaten, laesst sie fuer diese Nachricht bearbeiten und kopiert sie.
- Zeigt in Meine Matches und Meine Kandidaten unter dem Matchkommentar-Knopf "CEM To Do: 1", wenn OM einen Kommentar mit "CEM To Do:" geschrieben hat, den noch keine "CEM:"-Antwort erledigt. Im Matchkommentar-Dialog ist das To Do rot umrandet; Knoepfe ueber dem Textfeld schreiben die Antwort (ist/sind da mit Match senden oder nicht senden, angefragt, Abhaken).
- Erwähnt man im Kommentar-Editor jemanden, der heute vertreten wird, kommt die Vertretung als zweite Erwähnung direkt dahinter. Wer sie wieder löscht, bekommt sie nicht erneut. Ohne Toolbox taggt der n8n-Workflow Vertretungen Erwähnungen per Folgekommentar nach.
- Knopf „An KAM“ je Match in Meine Matches und Meine Kandidaten: schickt der KAM-Person des Arbeitgebers (und ihrer Vertretung) über den OPS-Bot eine Slack-DM mit Kandidat, Vakanz, Match-Link und optionalem Kommentar, unter deinem Namen. Der Dialog zeigt vorher, wer sie bekommt.
- Tooltip mit der Bedeutung, wenn die Maus im Matchkommentar-Dialog oder in AG-Notizen über einem KAM-Kürzel steht (tne, VTA, SA …).
- Knopf „@KAM“ in der Werkzeugleiste des Matchkommentar-Dialogs: erwähnt die KAM-Person des Arbeitgebers am Cursor. Rechtsklick öffnet die Auswahl aller KAM-Personen mit Suchfeld. Abgeschickt wird wie immer mit dem Pfeil.
- Ganz oben im Matchkommentar-Dialog der Hauptansprechpartner des Arbeitgebers mit Name, Telefonnummer und E-Mail, je mit Kopierknopf, dazu "Alles kopieren". Ohne markierten Haupt-AP steht der erste, mit Hinweis.
- Unter dem Ansprechpartner oben im Matchkommentar-Dialog die Arbeitgeberkommentare, neueste zuerst, nur lesend. Die neuesten 5, der Rest aufklappbar.
- Im Matchkommentar-Dialog an Stelle der Spalte "AG Fragebogen" der OM-Fragebogen des Matches, nur lesend: Anforderungen der Vakanz neben den Angaben des Kandidaten (Position, Berufserfahrung, Deutschkenntnisse, Führerschein, Auto, Reise-/Montagebereitschaft, Gehalt, Fachbereiche, Stellenumfang, Anerkennung, Entfernung) mit Bewertung passt/prüfen/passt nicht, darunter "Zusätzliche Information - OM". Der Haken "AG-Fragebogen anzeigen" blendet die native Spalte für diesen Dialog wieder ein.
- Feste VTA-Notiz je Arbeitgeber (z. B. Buchungslink): Box unter dem Notizfeld im Terminvorschlag-Dialog, bei neuen Terminen einmal ans Notizfeld angehängt. Pflege direkt in der Box oder im Tampermonkey-Menü. Gespeichert im n8n-Workflow VTA Notizen.
- Auch in KAM › Meine Matches steht der KAM-Out-Grund klein unter dem KAM-Status. In den CEM-Listen steht unter dem CEM Status der Grund (CEM-Out, KAM-Out und OM-Out bei "Nicht senden"), z. B. "CEM-Out: Entfernung zu weit". Ohne hinterlegten Grund "ohne Grund", Absagen aus der Kandidaten-App als "Absage in der App: ...".

## OBC Toolbox

[OBC-Toolbox.user.js](https://raw.githubusercontent.com/willywerkia/tampermonkey/main/OBC-Toolbox.user.js)

Enthaltene Funktionen:

- Prueft alle 5 Minuten, ob eine neuere Version der Toolbox veroeffentlicht ist, und bietet dann in einem kleinen Hinweis unten rechts Aktualisieren und Neu laden an. "Spaeter" blendet den Hinweis fuer vier Stunden aus.
- Kleine ?-Knoepfe an Dialogen, Leisten und Panels erklaeren die jeweilige Funktion. Der Hilfe-Knopf unten links und der Tampermonkey-Menueeintrag oeffnen eine Uebersicht aller Funktionen mit Kennzeichnung, ob sie nur anzeigen oder Daten aendern.
- Zeigt bei jedem Arbeitgeber ein Badge zur Antwortgeschwindigkeit (z. B. "Schnelle Rueckmeldung", "Keine Rueckmeldung").
- Markiert Zeilen von Arbeitgebern mit besonderer Absprache (GA-TEC) farblich mit Hinweistext "[Absprache vor OFM]".
- Markiert Vorschlaege, wenn beim Arbeitgeber bereits ein Match auf den Status "Senden" gestellt wurde. Bis 90 Tage bleibt die Zeile rot gefuellt, danach nur rot umrandet. Der Hinweis zeigt den Zeitpunkt der Statusaenderung und bei Reverse Matches den KAM-Status.
- Technische Hintergrundfunktion ohne eigene Anzeige - merkt sich Kandidat/Vakanz des offenen Fragebogens.
- Blendet neben dem Fragebogen ein Panel mit den oeffentlichen Vakanzangaben ein.
- Vergleicht Fragebogen-Antworten mit den Vakanzanforderungen und zeigt eine farbige Match-Entscheidungs-Empfehlung.
- Zeigt eine hervorgehobene Box mit den OM-Notizen zum Fragebogen direkt im Dialog.
- Zeigt beim offenen Fragebogen links zwischen OM-Notizen und Routenbox die Notizen der Vakanz (Additional Notes) an.
- Berechnet beim offenen Fragebogen Fahrzeit und Strecke zwischen Kandidatenwohnort und Arbeitsort, zeigt die Vakanzart und bei ortsgebundenen Vakanzen ab 50 Min einen Totenkopf.
- Zeigt im Fragebogen unter der Routenbox alle Matches des Kandidaten beim selben Arbeitgeber und bei Schwesterfirmen derselben Unternehmensgruppe, jeweils mit OM Status. Warnt, wenn ein anderer Match schon gesendet oder hochgeladen ist.
- Erlaubt auf Potenzielle Matches die Auswahl mehrerer Arbeitgeber und vorhandener Jobs für ein gemeinsames Offline-Match-Formular. Bei einem Arbeitgeber mit vorhandenem Match ist vor dem Öffnen eine Bestätigung nötig; Terminvorschläge lassen sich gesammelt löschen.
- Markiert dringend zu besetzende Vakanzen bei potenziellen Kandidaten-Matches farblich in der Liste.
- Zeigt getrennt erkennbare OM-Hinweise aus Arbeitgeber- und Vakanz-Notizen. Eindeutig verletzte Anforderungen und bereits gematchte Arbeitgeber lassen sich ausblenden; je Arbeitgeber bleiben hoechstens die ersten drei Matches in AP-Score-Reihenfolge sichtbar, auch ueber Seitenwechsel hinweg.
- Zeigt auf Potenzielle Matches in jeder Zeile die Fahrzeit vom Kandidatenwohnort zur Vakanz und die Vakanzart (Start von Zuhause, Landes-/bundesweit, Montage). Ortsgebundene Vakanzen ab 50 Min Fahrzeit bekommen einen Totenkopf. Hat der Kandidat mehrere Adressen, zaehlt die schnellste Route (wie im Fragebogen). Die Routen laden nacheinander im Hintergrund und bleiben eine Woche im Browser gespeichert.
- Dropdown ueber der Liste mit gespeicherten Filterkombinationen. "Aktuellen Filter speichern" uebernimmt Filter, Sortierung und Seitengroesse der Ansicht; Vorlagen liegen lokal im Browser und ueberstehen Toolbox-Updates.
- Warnt auf Potenzielle Matches, wenn ein vorgeschlagener Arbeitgeber bei diesem Kandidaten als No-Go hinterlegt ist - rot bei demselben Arbeitgeberprofil oder derselben Firmengruppe (gleicher Webauftritt), gelb bei einem blossen Namenstreffer, der noch geprueft werden muss.
- Erwähnt man im Kommentar-Editor jemanden, der heute vertreten wird, kommt die Vertretung als zweite Erwähnung direkt dahinter. Wer sie wieder löscht, bekommt sie nicht erneut. Ohne Toolbox taggt der n8n-Workflow Vertretungen Erwähnungen per Folgekommentar nach.
