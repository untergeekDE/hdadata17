# Sinnvolles von Sentinel: Wie man die Daten der Copernicus-Satelliten nutzt #

## Vorwort: Die ESA und die Daten 

Um es ganz klar zu sagen: **Die ESA hat datenjournalistische Projekte bis jetzt nicht wirklich auf dem Schirm**.

Der Abnehmer, an den die ESA-Forscher denken, sind andere Forscher - und lange Jahre war das ja auch so: alle, die
Zugang zu den Daten wollten, haben Monate bis Jahre aufgebracht, um sich (oder besser: ihre Doktoranden) in die Daten 
und Formate einzuarbeiten. Hoch spezialisierte Forschungsfragen sahen auf schmale Ausschnitte des Datenmaterials; Meteorologen
passten ihre Systeme an das verfügbare Datenmaterial an und rechneten damit ihre Prognosemodelle. Und für den Rest des Planeten 
produzierte die Pressestelle in regelmäßigen Abständen nette Folien und Stories zu ausgesuchten Datenpunkten. 

Den Anwendungsfall, dass vergleichsweise laienhafte Datennutzer damit Informations-Angebote von allgemeinem Interesse selbst 
erstellen, ist in der ESA-Denke bislang nicht wirklich vorgesehen - die Daten sind lausig dokumentiert, nicht besonders aufgearbeitet, 
in esoterischen Formaten versteckt. Die Frage von mir (und einer Journalisten-Kollegin der Stuttgarter Zeitung, die auf der Suche nach 
Daten zum Megathema Feinstaub im Stuttgarter Kessel ist), wer uns denn bei den ersten Schritten helfen könne, wird von der Digital-
Direktorin etwas gönnerhaft mit der Bemerkung beantwortet, die ESA wolle Raum für Startups und Firmen lassen, die sicher auch irgendwann
für unsere Anforderungen Daten produzieren würden; so einfach schöne Fotos zum Herunterladen habe die ESA jedenfalls nicht. Weil aber die 
ESA bislang nicht an Datenjournalismus gedacht hat, sind die Einstiegshürden für Datenjournalisten (noch) sehr hoch. 

Ein Beispiel: Die ESA-Wettervorhersage-Zentrale bietet nicht nur Prognosedaten, sondern auch historische Daten. Diese Daten stehen
laut Website "autorisierten Nutzern" zur Verfügung - auf Nachfrage erläutert mir der ECMWF-Mann, an sich könne man sich einfach anmelden, 
nur für die Prognose-Daten sei eine manuelle Freischaltung erforderlich. Und er erklärt, wie angemeldete Nutzer dann faktisch an Daten
kommen: Sie müssen sich nach der Anmeldung via Auswahl-Menü ein Python-Skript zusammenklicken - das lädt dann, wenn es auf dem Server des 
Nutzers ausgeführt wird, die Daten herunter, in einer NetCDF-Datei (ein Datenformat, das bei Meteorologen üblich ist). "Bei einem dieser
Schritte steigen die meisten unserer Kunden aus", gibt er freimütig zu. 

Immerhin: Für NetCDF hat Tableau einen Importfilter. Es ist also noch nicht aller Tage Abend!

Ganz abwegig ist auch der ESA-Hinweis auf die Startups nicht. Eine Reihe von Dienstleistern beschäftigt sich mit der Frage, wie
man die Daten in besser nutzbare Form bringen kann - neben dem Software-Riesen SAP, mit dem die ESA seit 2016 eine strategische Partnerschaft
hat, eine Reihe von Startups, aber auch die mit Bundesmitteln finanzierte Plattform CODE-DE. Dort ist auch das eine oder andere 
Tutorial zu finden - und es gibt auch Open-Source-Software zur Nutzung der Daten, die "Toolboxes", allerdings wenig dokumentiert. 

Der Aufwand ist hoch - aber er lohnt sich: Hier wartet wirklich Neuland. Und dass es noch kein einfaches "Sentinel-Daten verarbeiten für Dummies"-
Tutorial bei Youtube gibt, heißt auch: die Welt braucht Leute, die eins machen. Solche wie uns. 

## ESA, ESOC, EUMETSAT, ECMWF: Who's who?

- ESA: 
- ESOC: Das europäische Satellitenkontrollzentrum, die Missionszentrale für alle ESA-Missionen, in Darmstadt. 
- EUMETSAT: Internationale Organisation 30 europäischer Länder, die das METEOSAT-Programm betreibt. Sie kooperiert mit der ESA, ist aber von ihr
unabhängig. Die Satelliten-Kontrollzentrale für die Satelliten des METEOSAT-Programms ist in Darmstadt. 
- ECMWF: Agentur in London, die im EU-Auftrag die ESA-Daten weiterverarbeitet. Ursprünglich für Meteorologen - daher auch das Kürzel: "(E)uropean
(C)entre for (M)edium-range (W)eather (F)orecasts - inzwischen aber auf insgesamt sechs Sektoren tätig: Atmosphärenüberwachung, Meeresüberwachung, 
Landüberwachung, Klimawandel, Krisenmanagement, Sicherheit. 

## Die Satelliten ##

Das Copernicus-Programm ist kein Schnäppchen: seit 2014 sind die europäischen Satelliten in Betrieb, bis dahin haben sie 
die Steuerzahler rund 1,3 Milliarden Euro gekostet, bis 2020 werden es vermutlich weitere 4,3 Mrd. Euro sein. 

Das Copernicus-Programm ist ein Schnäppchen: Die ESA rechnet vor, dass die Investitionen in etwa der Hälfte von dem entsprechen, 
was ein Konzern wie Siemens im gleichen Zeitraum in Forschung und Entwicklung investiert - und dass sie einen extrem hohen 
Gewinn versprechen: [Eine Studie schätzt](http://www.copernicus.eu/sites/default/files/library/4_Copernicus_User_Uptake_Strategy.pdf), dass
die Daten im gleichen Zeitraum etwa 10 Mrd. an direktem volkswirtschaftlichem Nutzen produzieren - etwa durch Dienste, die die
Daten zur Verbesserung der Gesundheit oder zur Bekämpfung von Problemen nutzen - und dass außerdem ein "Downstream"-Nutzen in Höhe
von weiteren 3,5 Mrd. Euro entsteht - durch Innovationen, die im Umfeld des Satellitenprogramms möglich und nötig wurden. 

Beispiele für Use-Cases: 
- Luftverschmutzungs-Prognosekarten des ECMWF
- Eine Warn-App für Asthmatiker: wann besser nicht nach Peking (Berlin, Paris, London...) fahren?
- Eine UV-Warnkarte (des australischen Cancer Council Victoriy)
- Die Luftqualitäts-Vorhersage bei Euronews

### Sentinel-1
Sentinel-1 ist ein Bodenradar. 
Es gibt zwei Sentinel-Satelliten, 1A (seit 2014) und 1B (seit April 2016). 
Der Satellit tastet den Boden in 250km breiten Streifen (swathes) ab; 
die Auflösung beträgt 5x20m. Außerdem tastet er im “Stripmap”-Modus einen 80km breiten 
Streifen mit einer Auflösung von 5x5m ab. Im “Extra Wide Swath”-Modus tastet er mit einer Auflösung von 20x40m ab. 

Anwendungsgebiete: Eis-Messung, Ölverschmutzung, Seewinde, Landveränderung

Datensätze:

### Sentinel-2
Eine fliegende Kamera, die verschiedene Lichtspektren beobachtet - gerade die, die das menschliche Auge nicht sehen kann, und da
wird's interessant. ESA-Sprech: 
"SENTINEL-2 ist eine breitbandige, hochauflösende multispektrale Bildgebungs-Mission, die Copernicus Land Monitoring-Studien unterstützt, einschließlich der Überwachung von Vegetation, Boden und Wasser sowie der Beobachtung von Binnenwasserstraßen und Küstengebieten.
Das SENTINEL-2 Multispektral Instrument (MSI) wird 13 Spektralbänder erfassen: vier Bänder in 10 Metern, sechs Bänder in 20 Metern und drei Bänder in 60 Metern räumlicher Auflösung.
Die erhobenen Daten, Missionsabdeckung und hohe Wiederholungsfrequenz ermöglichen die Generierung von Geoinformationen auf lokaler, regionaler, nationaler und internationaler Ebene.
SENTINEL-2-Daten ergänzen bestehende Missionen, einschließlich LANDSAT (siehe Abbildung 1) und SPOT. Die Daten sind so konzipiert, dass sie von Nutzern geändert und angepasst werden können, die sich für Themenbereiche interessieren, wie:"
- Raumplanung
- Agrarumweltüberwachung
- Wasserüberwachung
- Überwachung von Wald und Vegetation
- Land Kohlenstoff, Überwachung natürlicher Ressourcen
- globale Ernteüberwachung

Die Daten umfassen:
- Bilddaten in Granulat oder Kacheln und das Produkt Area of ​​Interest (AOI) abdecken
- Vorschau-Daten, die einen Überblick über das Produkt für nachfolgende Bildsuche und Benutzerauswahl Zwecke bietet
- Zusatzdaten aus der Satellitentelemetrie
- Hilfsdateninformation, die die verwendeten Parameter beschreibt
- Qualitätsindikatordaten, die das Produkt in Bezug auf radiometrische, geometrische und Bildeigenschaften beschreiben.

### Sentinel-3

Sentinel-3 ist: 
- eine große Kamera
- ein Bodenradar
- ein fliegendes Thermometer. 

Oder, im ESA-Sprech: “SENTINEL-3 ist eine europäische Satellitenmission zur Erdbeobachtung, 
die entwickelt wurde, um GMES-Anwendungen in den Bereichen Ozean, Land, Atmosphäre, Notfall, Sicherheit und Kryosphäre zu unterstützen.”

Datensätze: 
- Wärmedaten, 
- Oberflächentemperatur
- Oberflächenprofil (Radar-Abtastung erkennt Berge, Täler, Gebäude?)
- Wassertemperatur
- Kameras, die Vegetationen erkennen

### Sentinel-5P
Misst Atmosphärengase und Aerosole; kann also Aussagen über die Luftqualität und über Atmosphärenbedingungen 
(Wolken!) liefern. “This means that a wide range of pollutants such as nitrogen dioxide, ozone, formaldehyde,
sulphur dioxide, methane and carbon monoxide can be imaged more accurately than ever before.
With a resolution as high as 7 km × 3.5 km, it has the potential to detect air pollution over individual cities.”

Datensätze:
Ausgewertete Daten über Atmosphärendaten - Level 2 (liegen mit 5 Tagen Verzögerung vor) 
- Methan
- Ozon
- SO2 Stickoxid
 
## Daten laden




## Erste Anlaufstellen ##

- [**CODE-DE**](http://code-de.org) ist ein vom Bundesforschungsministerium bezahltes Datenportal für Sentinel-1 und Sentinel-2. 
- [**Sentinel Playground**](http://apps.sentinel-hub.com/sentinel-playground/) Demo-Anwendung mit Sentinel-2-Daten eines slowenischen
Startups, das die Sat-Karten aufbereitet und vermarktet
