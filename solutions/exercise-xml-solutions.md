# 📄 XML Übungen - Musterlösungen

## ✅ Lösung zur Aufgabe XML 1

```xml
<!ELEMENT MODell (#PCDATA)>
<!ELEMENT Hersteller des Autos (#PCDATA)> <!-- Leerzeichen im Elementnamen sind nicht erlaubt -->
<!ELEMENT Jahr_des_Bauens (#PCDATA)>
<!ELEMENT Bemerkungen_12neu (#PCDATA)>
<!ELEMENT 12_Hallo (#PCDATA)> <!-- Darf nicht mit Zahl beginnen -->
<!ELEMENT Tim&Struppi (#PCDATA)> <!-- & ist verboten -->
```

## ✅ Lösung zur Aufgabe XML 2

```xml
<?xml version='1.0' standalone='no'?>
<?xml-stylesheet type="text/xsl" href="gruppen.xsl"?>
<gruppe id='E'>
    <team id='GER'>
        <land>Deutschland
        <trainer>Voeller</land></trainer> <!-- falsche Schachtelung -->
        <spiele>3</spiele>
        <punkte>7</punkte>
    </team>
</gruppe>
<gruppe> <!-- es darf nur ein Wurzel-Element geben -->
    <team id='IRL'>
        <land>Irland</land>
        <trainer>Mc Carthy</trainer>
        <spiele>3</spiele>
        <punkte>5</Punkte> <!-- Gross- und Kleinschreibung beachten -->
    </team>
    <team id="CMR">
        <land>Kamerun</land>
        <trainer>Schaefer</trainer>
        <spiele>3</spiele>
        <punkte>4</punkte><HR> <!-- End-Tag fehlt -->
    </team>
    <team id=KSA> <!-- Attribute gehören in Hochkomma -->
        <land>Saudi Arabien</land>
        <trainer>Al Johar</coach> <!-- Start- und End-Tag sind verschieden -->
        <spiele>3</spiele>
        <punkte>0<punkte> <!-- Slash im End-Tag fehlt -->
    </team>
</gruppe>
```

## ✅ Lösung zur Aufgabe XML 3

```xml
<!DOCTYPE CDSAMMLUNG [
    <!ELEMENT CDSAMMLUNG (Datensatz)+>
    <!ELEMENT Datensatz (Kuenstler, Titel, Jahr)>
    <!ELEMENT Kuenstler (#PCDATA)>
    <!ELEMENT Titel (#PCDATA)>
    <!ELEMENT Jahr (#PCDATA)>
]>
<CDSAMMLUNG> <!-- 1. Fehler: Wurzelelement fehlt -->
    <Album>
        <Kuenstler>Eros Ramazotti</Kuenstler>
        <Titel>Perfetto</Titel> <!-- 2. Fehler: falscher End-Tag -->
        <Jahr>2015</Jahr> <!-- 3. Fehler: Jahr groß schreiben-->
    </Album>
    <Album>
        <Kuenstler>Elli Goulding</Kuenstler> <!-- 4. Slash fehlt -->
        <Titel>Bright Lights</Titel>
        <Jahr>2010</Jahr>
    </Album> <!-- 5. Fehler: End-Tag fehlt -->
</CDSAMMLUNG>
```

## ✅ Lösung zur Aufgabe XML 4

```xml
<adressbuch>
    <bezeichnung><![CDATA[Mein erstes <XML>Adressbuch]]></bezeichnung>
    <adresse id="A1">
        <vorname>Max</vorname>
        <nachname>Müller</nachname>
        <email>max@mueller.de</email>
        <telefon land="" vorwahl="0721">6669888</telefon>
        <notiz>Mein bester Freund</notiz>
    </adresse>
    <adresse id="A2">
        <vorname>Martina</vorname>
        <nachname>Kramer</nachname>
        <email>martina@kramer.de</email>
        <telefon land="+34" vorwahl="309">229922</telefon>
        <notiz>Freundin meines Bruders</notiz>
    </adresse>
</adressbuch>
```

## ✅ Lösung zur Aufgabe XML 5

```xml
<!DOCTYPE adressbuch SYSTEM "Adressen1.dtd">
<adressbuch>
    <bezeichnung><![CDATA[Mein erstes <XML>Adressbuch]]></bezeichnung>
    <adresse id="A1">
        <vorname>Max</vorname>
        <nachname>Müller</nachname>
        <email>max&at;mueller.de</email>
        <telefon vorwahl="0721">6669888</telefon>
        <notiz>Mein bester Freund</notiz>
    </adresse>
    <adresse id="A2">
        <vorname>Martina</vorname>
        <nachname>Kramer</nachname>
        <email>martina&at;kramer.de</email>
        <telefon land="+34" vorwahl="309">229922</telefon>
    </adresse>
</adressbuch>
```

**DTD-Datei (Adressen1.dtd):**
```xml
<!ELEMENT adressbuch (bezeichnung, adresse+)>
<!ELEMENT bezeichnung (#PCDATA)>
<!ELEMENT adresse (vorname, nachname, email, telefon, notiz?)>
<!ATTLIST adresse
    id ID #REQUIRED
>
<!ELEMENT email (#PCDATA)>
<!ELEMENT vorname (#PCDATA)>
<!ELEMENT nachname (#PCDATA)>
<!ELEMENT notiz (#PCDATA)>
<!ELEMENT telefon (#PCDATA)>
<!ATTLIST telefon
    land CDATA #IMPLIED
    vorwahl CDATA #REQUIRED
>
<!ENTITY at "@">
```

## ✅ Lösung zur Aufgabe XML 6

**DTD Bibliothek:**
```xml
<!-- DTD Bibliothek -->
<!ELEMENT Bib (Buch)+>
<!ELEMENT Buch (Titel, Autor*, Verlag)>
<!ATTLIST Buch ISBN CDATA #REQUIRED>
<!ELEMENT Titel (#PCDATA)>
<!ELEMENT Autor (Vorname, Nachname, Organisation?)>
<!ELEMENT Vorname (#PCDATA)>
<!ELEMENT Nachname (#PCDATA)>
<!ELEMENT Organisation (#PCDATA)>
<!ELEMENT Verlag (#PCDATA)>
```