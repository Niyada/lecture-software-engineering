# 📄 Übungen XML

Diese Aufgaben führen Sie in die Grundlagen von XML und DTD ein.

## 📝 Aufgabe 1️⃣

Welche der folgenden Tag-Namen sind falsch?

```text
<!ELEMENT MODell (#PCDATA)>
<!ELEMENT Hersteller des Autos (#PCDATA)>
<!ELEMENT Jahr_des_Bauens (#PCDATA)>
<!ELEMENT Bemerkungen_12neu (#PCDATA)>
<!ELEMENT 12_Hallo (#PCDATA)>
<!ELEMENT Tim&Struppi (#PCDATA)>
```


## 🔍 Aufgabe 2️⃣

Prüfen Sie das folgende XML-Dokument auf Wohlgeformtheit. Streichen Sie alle Fehler an und begründen Sie kurz, warum es ein Fehler ist.

```xml
<?xml version='1.0' standalone='no'?>
<?xml-stylesheet type="text/xsl" href="gruppen.xsl"?>
<gruppe id='E'>
    <team id='GER'>
        <land>Deutschland
        <trainer>Voeller</land></trainer>
        <spiele>3</spiele>
        <punkte>7</punkte>
    </team>
</gruppe>
<gruppe>
    <team id='IRL'>
        <land>Irland</land>
        <trainer>Mc Carthy</trainer>
        <spiele>3</spiele>
        <punkte>5</Punkte>
    </team>
    <team id="CMR">
        <land>Kamerun</land>
        <trainer>Schaefer</trainer>
        <spiele>3</spiele>
        <punkte>4</punkte><HR>
    </team>
    <team id=KSA>
        <land>Saudi Arabien</land>
        <trainer>Al Johar</coach>
        <spiele>3</spiele>
        <punkte>0<punkte>
    </team>
</gruppe>
```


## ✅ Aufgabe 3️⃣

Prüfen Sie das folgende XML-Dokument auf Gültigkeit in Bezug auf die vorgegebene DTD. Streichen Sie alle fünf Fehler an und begründen Sie kurz, warum es ein Fehler ist bzw. wie dieser in der XML Datei korrigiert werden sollte.

```xml
<!DOCTYPE CDSAMMLUNG [
    <!ELEMENT CDSAMMLUNG (Album)+>
    <!ELEMENT Album (Kuenstler, Titel, Jahr)>
    <!ELEMENT Kuenstler (#PCDATA)>
    <!ELEMENT Titel (#PCDATA)>
    <!ELEMENT Jahr (#PCDATA)>
]>
<Album>
    <Kuenstler>Eros Ramazotti</Kuenstler>
    <Titel>Perfetto</Title>
    <jahr>2015</jahr>
</Album>
<Album>
    <Kuenstler>Elli Goulding<Kuenstler>
    <Titel>Bright Lights</Titel>
    <Jahr>2010</Jahr>
</CDSAMMLUNG>
```


## 🛠️ Aufgabe 4️⃣

Schreiben Sie ein XML-Dokument, das ein Adressbuch abspeichern soll. Das Adressbuch enthält eine Bezeichnung (z.B. "Adressen meiner Freunde"). Jede Adresse besteht aus einer eindeutigen ID, den Feldern Vorname, Nachname, Email, Telefon und Notiz. Die Telefonnummer wird über die Attribute land und vorwahl strukturiert.

Verwenden Sie die folgenden Datensätze als Inhalt:
- **Bezeichnung des Adressbuchs:** Mein erstes <XML>-Adressbuch
- **Datensatz A1:** Max Müller, 0721 6669888, max@mueller.de, 1.10.1970, Mein bester Freund
- **Datensatz A2:** Martina Kramer, +34309229922, martina@kramer.de, Freundin meines Bruder

Prüfen Sie das Dokument mit einem Browser auf Wohlgeformtheit.

## 📋 Aufgabe 5️⃣

Entwickeln Sie passend zu Aufgabe 4 eine DTD, die die folgenden Angaben zur Struktur enthält:  
- Mindestens eine Adresse muss enthalten sein
- Jede Adresse ist eindeutig
- Nicht jede Adresse muss eine Notiz beinhalten
- Die Landesvorwahl ist optional
- Das @-Zeichen wird durch eine Entity definiert, sodass im XML-Dokument die Zeichenfolge &at; wieder zu einem @-Zeichen aufgelöst wird.

Binden Sie die DTD in das XML-Dokument aus Aufgabe 4 ein.  
Prüfen Sie Ihr Dokument auf Gültigkeit, z.B. mit dem XML Validierer unter http://www.xmlvalidation.com!


## 📚 Aufgabe 6️⃣

Schreiben Sie für die folgende XML-Datei eine passende DTD-Datei.

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<Bib>
    <Buch ISBN='3836226200'>
        <Titel>Einstieg in XML</Titel>
        <Autor>
            <Vorname>Helmut</Vorname>
            <Nachname>Vonhoegen</Nachname>
        </Autor>
        <Verlag>Galileo Computing</Verlag>
    </Buch>
    <Buch ISBN='3446440739'>
        <Titel>Grundkurs Programmieren in Java</Titel>
        <Autor>
            <Vorname>Dietmar</Vorname>
            <Nachname>Ratz</Nachname>
            <Organisation>DHBW</Organisation>
        </Autor>
        <Autor>
            <Vorname>Jens</Vorname>
            <Nachname>Scheffler</Nachname>
        </Autor>
        <Autor>
            <Vorname>Delef</Vorname>
            <Nachname>Seese</Nachname>
        </Autor>
        <Autor>
            <Vorname>Jan</Vorname>
            <Nachname>Wiesenberger</Nachname>
        </Autor>
        <Verlag>Carl Hanser Verlag</Verlag>
    </Buch>
</Bib>
```

Binden Sie Ihre DTD in das XML-Dokument ein.

Prüfen Sie Ihr Dokument auf Gültigkeit, mit einem online XML Validierer, z.B. [diesem hier](https://www.truugo.com/xml_validator/).
