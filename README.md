Konzeption und Prototyping einer mobilen Web-Anwendung zur standortbasierten Lichtanalyse für Zimmerpflanzen
Einleitung
Die korrekte Platzierung von Zimmerpflanzen entsprechend ihrer spezifischen Lichtbedürfnisse stellt für viele Pflanzenfreunde eine zentrale Herausforderung dar. Subjektive Einschätzungen von Lichtverhältnissen wie "sonnig", "halbschattig" oder "schattig" sind oft ungenau und führen zu suboptimalen Wachstumsbedingungen. Die vorliegende Arbeit beschreibt die Konzeption und das Prototyping einer mobilen Web-Anwendung, die Nutzern eine datengestützte und präzise Analyse der Lichtverhältnisse an einem beliebigen Standort in Innenräumen ermöglicht. Ziel ist es, durch die Kombination von Gerätesensorik und astronomischen Berechnungen eine fundierte Entscheidungsgrundlage für die Wahl des optimalen Pflanzenstandorts zu schaffen.

1. Nutzen und Zielsetzung
Der primäre Nutzen der Anwendung liegt in der Objektivierung der Standortwahl für Zimmerpflanzen. Anstatt sich auf vage Schätzungen zu verlassen, erhalten Nutzer quantifizierbare Daten, die ihnen helfen, die Lebensbedingungen ihrer Pflanzen signifikant zu verbessern. Dies führt zu gesünderem Pflanzenwachstum, beugt Schäden durch Lichtmangel oder -überschuss vor und steigert somit nachhaltig die Freude an der Pflanzenpflege.

Die Zielsetzung des Projekts gliedert sich in zwei Kernfunktionen:

Quantitative Lichtmessung: Die App soll die exakte Beleuchtungsstärke (lx) an einem Punkt erfassen und diese in für Laien verständliche Kategorien (Schatten, Halbschatten, Sonne) übersetzen.
Prädiktive Standortanalyse: Die App soll eine qualitative Bewertung von Fensterseiten ermöglichen, indem sie die Himmelsrichtung erkennt und den Sonnenverlauf für den aktuellen Tag und Standort prognostiziert. Dies erlaubt eine strategische Planung, auch wenn die Sonne gerade nicht scheint.
Durch die Kombination dieser beiden Funktionen wird die Anwendung zu einem multifunktionalen Werkzeug, das sowohl reaktive Messungen als auch proaktive Planungen unterstützt.

2. Inhaltliches Konzept und Funktionsumfang
Die Anwendung ist als Progressive Web App (PWA) konzipiert, die direkt im mobilen Browser läuft und keinen Download aus einem App-Store erfordert. Der Funktionsumfang ist in zwei Hauptmodule gegliedert.

2.1 Modul 1: Lichtstärkenmessung
Dieses Modul dient der Ad-hoc-Analyse eines Standorts. Der Nutzer platziert sein Smartphone am gewünschten Ort (z.B. auf einer Fensterbank) und initiiert die Messung per Knopfdruck. Die Anwendung greift auf den Umgebungslichtsensor des Geräts zu und liefert folgende Ausgaben:

Numerischer Lux-Wert: Die exakte Beleuchtungsstärke in Lux.
Kategorisierung: Eine Interpretation des Werts in den Kategorien "Schattig" (<5.000lx), "Halbschatten" (5.000−20.000lx) und "Sonnig" (>20.000lx).
Visuelles Feedback: Ein Emoji (🌒, ⛅️, ☀️) zur schnellen Erfassung der Lichtsituation.
2.2 Modul 2: Sonnenverlaufs- und Himmelsrichtungsanalyse
Dieses Modul dient der strategischen Planung und Identifizierung geeigneter Fensterseiten. Es nutzt eine Kombination aus Geodaten und dem digitalen Kompass des Geräts.

Standort- und Sensorzugriff: Die Funktion wird durch einen Button aktiviert, woraufhin der Nutzer um Freigabe seines Standorts und der Bewegungssensoren gebeten wird.
Live-Kompass: Die Anwendung zeigt die Himmelsrichtung (N, O, S, W etc.) an, in die das Smartphone aktuell gehalten wird.
Standortanalyse: Basierend auf der erkannten Himmelsrichtung gibt die App eine qualitative Einschätzung über die zu erwartende Sonneneinstrahlung im Tagesverlauf ab (z.B. "Süden: Stärkste, meiste Sonne. Ideal für Sonnenanbeter."). Diese Analyse basiert auf allgemeinen astronomischen Gegebenheiten der jeweiligen Hemisphäre.
3. Technische Konzeption und Realisierung
Die Realisierung des Prototyps erfolgte als in sich geschlossene Web-Anwendung unter Verwendung moderner Web-Technologien.

3.1 Technologiestack
HTML5: Dient als semantisches Grundgerüst für die Struktur der Anwendung.
CSS3: Verantwortlich für das visuelle Design (Styling) und ein responsives Layout, das sich an mobile Endgeräte anpasst.
JavaScript (ES6+): Bildet die logische Schicht der Anwendung. Hier werden die Sensordaten verarbeitet, Berechnungen durchgeführt und die Benutzeroberfläche dynamisch manipuliert.
3.2 Genutzte Web-APIs und Sensordaten
Die Kernfunktionalität basiert auf dem Zugriff auf standardisierte Browser-APIs, die eine Schnittstelle zur Hardware des Geräts bereitstellen. Der Zugriff erfordert stets eine sichere Verbindung (HTTPS) und die explizite Zustimmung des Nutzers (Permissions).

Ambient Light Sensor API: Ermöglicht den Zugriff auf den Umgebungslichtsensor des Geräts, um die Beleuchtungsstärke in Lux auszulesen. Die Implementierung erfolgte über das AmbientLightSensor-Objekt.
Geolocation API: Wird genutzt, um die geografischen Koordinaten (Breiten- und Längengrad) des Nutzers via navigator.geolocation zu ermitteln. Diese Daten sind die Grundlage für standortspezifische Berechnungen.
Device Orientation API: Liefert Daten von den Bewegungssensoren des Geräts. Für die Kompassfunktion wird das deviceorientationabsolute-Event genutzt, dessen alpha-Wert die Ausrichtung relativ zum magnetischen Norden (0-360°) angibt.
3.3 Externe Bibliotheken
Für die komplexe Berechnung des Sonnenstandes wurde auf eine spezialisierte Bibliothek zurückgegriffen, um Entwicklungszeit zu sparen und die Genauigkeit zu gewährleisten.

SunCalc.js: Eine leichtgewichtige und hochpräzise JavaScript-Bibliothek zur Berechnung von Sonnen- und Mondpositionen. Sie wird im Prototyp zur potenziellen Berechnung von Sonnenauf- und -untergangszeiten sowie des Sonnenstandes zu jeder Tageszeit eingesetzt. Im aktuellen Prototyp wird die Analyse noch durch eine vereinfachte Logik abgebildet, die Bibliothek ist jedoch für den Ausbau bereits integriert.
3.4 Hosting und Deployment
Während des Prototypings wurde festgestellt, dass Hosting-Plattformen wie CodePen, die Code in <iframe>-Elementen ausführen, den Sensorzugriff über eine restriktive Permissions Policy blockieren. Die Lösung war der Umstieg auf die Plattform Glitch, die das Projekt unter einer eigenen Subdomain hostet und somit die notwendigen Berechtigungen für den Sensor- und Standortzugriff ermöglicht.

4. Erweiterungspotenziale und Ausblick
Der realisierte Prototyp stellt eine solide Basis dar und validiert das Kernkonzept. Folgende Erweiterungen sind denkbar:

Integration einer Pflanzendatenbank: Nutzer könnten ihre Pflanze auswählen, und die App würde den gemessenen Wert direkt mit den Bedürfnissen der Pflanze abgleichen.
Detaillierte Sonnenverlaufs-Visualisierung: Statt einer reinen Textanalyse könnte der Sonnenverlauf (Azimut, Höhe) für den Tag grafisch als Bogen über einem Kompass dargestellt werden.
Langzeitmessung: Eine Messung über einen längeren Zeitraum (z.B. 60 Minuten) könnte Durchschnitts- und Spitzenwerte ermitteln, um ein umfassenderes Bild der Lichtverhältnisse zu geben.
Augmented Reality (AR): Eine AR-Ansicht könnte den berechneten Sonnenverlauf direkt über das Kamerabild des Raumes legen und so visualisieren, wann die Sonne durch ein bestimmtes Fenster scheinen wird.
5. Fazit
Der Prototyp demonstriert erfolgreich, dass eine präzise und nutzerfreundliche Lichtanalyse für Pflanzenstandorte allein mit den Mitteln moderner Web-Browser realisierbar ist. Durch die intelligente Verknüpfung von Sensordaten und astronomischen Berechnungen wird ein signifikanter Mehrwert für den Endnutzer geschaffen. Die im Entwicklungsprozess identifizierten Hürden, wie die Permissions Policy von Hosting-Umgebungen, unterstreichen die Bedeutung der Wahl der richtigen Deployment-Strategie für hardwarenahe Web-Anwendungen. Das Projekt besitzt erhebliches Potenzial für den Ausbau zu einer umfassenden Planungs- und Verwaltungs-App für Pflanzenliebhaber.
