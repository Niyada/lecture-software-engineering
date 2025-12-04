# 🌐 Übungsblatt HTML und CSS

In der Vorlesung wurden nur einzelne Elemente von HTML und CSS vorgestellt. Bitte verwenden Sie zur Lösung der Aufgaben entsprechende Online-Ressourcen (z.B. [selfhtml](https://wiki.selfhtml.org/wiki/HTML) oder [W3Schools](https://www.w3schools.com/html/default.asp) bzw. weiterführende Bücher. Die Dokumente sollten HTML5-konform sein und es sollen, wo möglich, HTML5 Elemente zur semantischen Auszeichnung verwendet werden.

> [!NOTE]
> Semantische HTML5-Elemente verbessern die Zugänglichkeit und das SEO-Ranking Ihrer Webseite:
> ```html
> <!-- ❌ Nicht semantisch -->
> <div class="header">...</div>
> 
> <!-- ✅ Semantisch korrekt -->
> <header>...</header>```


## 📝 Aufgabe 1️⃣ (HTML Einstieg)

Erstellen Sie eine Startseite, die eines Ihrer Hobbys beschreibt. Die Datei hat einen Kopfteil (`header`), Rumpf (`body`) und eine Fußzeile (`footer`).

• **Header:** Der Titel soll den Namen des Hobbys beinhalten  
• **Der Rumpf** ist in drei Bereiche eingeteilt. Als erstes wird das Hobby allgemein beschrieben und dann stellen Sie Ihr Engagement oder Ihren Verein vor. Benutzen Sie dafür verschiedene Überschriften und Listen. Erstellen Sie mindestens zwei Links zu weiterführenden Webseiten.  
• **In der Fußzeile** stellen Sie Kontaktdaten zur Verfügung.

## 🖼️ Aufgabe 2️⃣ (HTML, Medien einbinden)

Erweitern Sie Ihre Webseite mit Fotos oder Videos. Setzen Sie bei den Medien das alt Attribut und den Tooltip (mittels des `title` Attribut: [siehe hier](https://www.w3schools.com/tags/att_global_title.asp)) ein. Experimentieren Sie mit festen und flexiblen Größenangaben sowie verschiedenen Positionsmöglichkeiten (z.B. oberhalb oder text-umschließend).

Ergänzen Sie ein (fiktives, z.B. generiertes) Gruppenbild. Experimentieren Sie mit einer [Image Map](https://www.w3schools.com/html/html_images_imagemap.asp), so dass beim Klicken auf den Kopf einer Person im Bild eine neue Webseite mit dem Namen und Informationen zu eben dieser Person angezeigt wird.

## 🎨 Aufgabe 3️⃣ (HTML, CSS)

Erstellen Sie zu Ihrer Webseite CSS Code, der die folgenden Einstellungen definiert:

- Die Hintergrundfarbe der Seite
- Eine einheitliche Schriftart
- Überschriften sollen alle grün und zentriert sein
- Jeder Abschnitt wird durch einen Rahmen mit der Breite von `5px` umgeben
- Die Rahmenfarbe ist grün
- Der Abstand zwischen den Rahmen ist `10px` und der Innenabstand ist `20px`

> [!TIP]
> Auch für CSS gibt es zahlreiche Online-Ressourcen, z.B. [selfhtml CSS](https://wiki.selfhtml.org/wiki/CSS) oder [W3Schools CSS](https://www.w3schools.com/css/default.asp).

## 📊 Aufgabe 4️⃣ (HTML (Tabellen), CSS)

Erstellen Sie die folgende Website die eine HTML-Tabelle enthält:

![Bild der zu erstellenden Website](/exercises/media/exercise-html-css-task-4-table.png)

Sie weist folgende Eigenschaften auf:
- Die Hintergrundfarbe der Überschrift ist Grau. Der text ist zentriert und die Schriftfarbe ist weiß.
- Die Tabelle sowie die Überschrift haben eine feste Breite von `420` Pixel
- Hintergrundfarbe der Tabelle ist hellgelb  
- Die Tabelle ist mit einer `5` Pixel starken (dicken) gestrichelten blauen Linie umgeben  
- Tabellenspalten haben einen Innenabstand von `5` Pixel  
- Die Überschrift in der Tabelle ist mit einem gepunkteten schwarzen Rahmen mit einer Dicke von `3` Pixel umgeben  
- Die Inhalte der Zellen sind zentriert und mit grau oder hellgrün hinterlegt
- Die Inhalte der Zellen der Spalten 'Straße', 'PLZ' und 'Ort' haben einen linken Innenabstand von `10` Pixel

> [!TIP]
> Sie können die eine Farbpalette, wie z.B. [MaterialUI](https://materialui.co/colors) verwenden, um angenehme Farben auszuwählen.

## 🛒 Aufgabe 5️⃣ (HTML (Shop), CSS)

Erstellen Sie eine HTML-Datei, die die folgende Webseite darstellt und die durch ein **extern eingebundenes** CSS formatiert wird:

![Bild der zu erstellenden Website](/exercises/media/exercise-html-css-task-5-website.png)

- Aller Text soll als `sans-serif` Schriftart dargestellt werden.
- Der Titel "Sportschuh" soll zentriert und fett dargestellt werden.
- Das Bild soll 
  - eine dynamische Breite von `30%` haben und 
  - eine automatisch angepasste Höhe haben
- Die Produktbeschreibung wird 
  - rechts neben den Bild angezeigt 
  - hat einen Zeilenabstand von `1.5em`
- Das Bestellformular soll
  - unterhalb der Produktbeschreibung angezeigt werden
  - die Voreinstellung so gewählt werden, dass der Artikel 1x in der Größe 38 bestellt wird
  - alle Bestelldaten an eine Email-Adresse schicken
-  es können maximal `10` Artikel und mindestens `1` Artikel bestellt werden

> [!TIP]
> Verwenden Sie für die Aktion des Formulars `mailto:`, um die Bestelldaten per E-Mail zu versenden.

> [!TIP]
> Sie können zum Erstellen des Layouts der Website die in der Vorlesung kennen gelernten Tabellen verwenden, order Sie verwenden das modernere CSS Flexbox Layout: [CSS Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
