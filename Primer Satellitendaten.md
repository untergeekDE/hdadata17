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

- ESA: Die Europäische Raumfahrtorganisation - 22 Mitgliedsstaaten, darunter mit Norwegen auch ein Nicht-EU-Staat
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

####Level-1-Produkte: 
##### SLC - Single-Look Complex
focused SAR data, geo-referenced using orbit and attitude data from the satellite, and provided in slant-range geometry. Slant range is the natural radar range observation coordinate, defined as the line-of-sight from the radar to each reflecting object. The products are in zero-Doppler orientation where each row of pixels represents points along a line perpendicular to the sub-satellite track.
##### GRD - Ground-Range Detection
products consist of focused SAR data that has been detected, multi-looked and projected to ground range using the Earth ellipsoid model WGS84. The ellipsoid projection of the GRD products is corrected using the terrain height specified in the product general annotation. The terrain height used varies in azimuth but is constant in range (but can be different for each IW/EW sub-swath).
####Level-2-Produkte:
##### OCN - Ocean
    Ocean Wind field (OWI)
    Ocean Swell spectra (OSW)
    Surface Radial Velocity (RVL)
Die Meeresdaten - mehr: https://sentinels.copernicus.eu/web/sentinel/user-guides/sentinel-1-sar/product-types-processing-levels/level-2

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

####Level-2
##### BOA - Bottom of Atmosphere
Satellitenfotos. Eigentlich ein Kunstprodukt - das von der Sentinel-Toolbox (bzw. anderen "Prozessoren") aus den Level-1C-Produkten errechnet wird. https://sentinels.copernicus.eu/web/sentinel/user-guides/sentinel-2-msi/product-types/level-2a

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

Sentinel-3 besteht aus 2 Systemen: 
- OLCI (Ocean Land Colour Instrument), einer Multiband-Kamera https://sentinels.copernicus.eu/web/sentinel/technical-guides/sentinel-3-olci/olci-instrument
- SLSTI (Sea and Land Surface Temperature Radiometer), einem Bodenradar https://sentinels.copernicus.eu/web/sentinel/technical-guides/sentinel-3-slstr/instrument/description

####Level-1-Daten
####Level-2-Daten
##### 
#####
#####
#####

    SL_2_WCT gathers the results from the Sea Surface Temperature (SST) processing (see algorithms), i.e. SST (single and dual view, 2 and 3 channels). This product is an internal product and is not available to users.
    SL_2_WST gathers the results from L2P processing (see algorithms), i.e. the GHRSST like L2P SST.
    SL_2_LST gathers the results from Land Surface Temperature (LST) processing (see algorithms), i.e. the LST.
    SL_2_FRP gathers the results from Fire Radiative Power (FRP) processing (see algorithms), i.e. the FRP.
    SL_2_AOD gathers the results from Aerosol Optical Depth (AOD) processing (see algorithms), i.e. the AOD
    
    OLCI:
https://sentinels.copernicus.eu/web/sentinel/technical-guides/sentinel-3-olci/level-2/products-description

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

## Level-2-Produkte

## Daten laden

- wohl in der Regel im Datenformat NetCDF (ein Datenformat, das bei Meteorologen üblich ist)
- Die Dateien sind in der Regel mehrere GB groß
- Beim ECMWF gibt es auch aufgearbeitete Daten, u.a. Prognosen - allerdings kann man die nicht einfach herunterladen, sondern muss sich einen Downloader als Python-Skript zusammenklicken. 
- In der Regel: Anmeldung erforderlich. 

## Erste Anlaufstellen ##

- [**CODE-DE**](http://code-de.org) ist ein vom Bundesforschungsministerium bezahltes Datenportal für Sentinel-1 und Sentinel-2. 
- [**Sentinel Playground**](http://apps.sentinel-hub.com/sentinel-playground/) Demo-Anwendung mit Sentinel-2-Daten eines slowenischen
Startups, das die Sat-Karten aufbereitet und vermarktet
- SAP HANA - ein Kooperationsprojekt, das aufgearbeitete Daten zur Verfügung stellt, über APIs und cloudbasierte Datendienste. [Presseinfo (mit Pressekontakt, evtl. anfragen)](https://news.sap.com/germany/sap-hana-esa-muenchner-rueck/)

## Tools ##

- Von der ESA: SNAP, die "Sentinel Application Platform". [Tutorial-Seite auf der "Science Toolbox Exploitation Platform" (STEP)](http://step.esa.int/main/doc/tutorials/snap-tutorials/).
- QGIS, ein Open-Source-Tool zur Visualisierung von Geodaten. [Hier ein Geodaten-Tutorial einer Consultingfirma](https://www.lutraconsulting.co.uk/blog/2017/11/02/working-with-climate-data-in-qgis/).
- [Benutzerhandbuch SENTINEL CODE-DE (PDF)](https://code-de.org/de/manuals/CD-UM-3301DE_Benutzerhandbuch_v1.1_online.pdf)
- [Die FAQ zur Web-API](https://software.ecmwf.int/wiki/display/WEBAPI/Web-API+FAQ) der ECMWF (s.o.)
