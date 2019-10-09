# 2. Übungsblatt 2: Information (Musterlösung)

<!-- Chapter: 2 -->

## 2.1 Pi als Nachricht
Lässt sich die Zahl π als Nachricht übermitteln? Begründen Sie Ihre Antwort.

*Lösung:*
Die Zahl π ist eine reelle Zahl, und zwar eine transzendente Zahl mit unendlich vielen Stellen, deren Folge kein periodisches Muster bildet. Da von einer Nachricht gefordert werden muss, dass sie aus einer abzählbaren Folge von Einzelzeichen bestehen muss, kann π genau genommen nicht als Nachricht übermittelt werden. Man kann jedoch einen Näherungswert von π mit beliebig vielen Stellen übermitteln, oder auch eine Rechenvorschrift, die dem Empfänger prinzipiell die Berechnung beliebig vieler Stellen von π erlaubt.

## 2.2 Atome im Universum
Schätzungen zufolge besteht das Universum aus einer Tredezillion Atomen (10^78). Welche Bitbreite ist mindestens notwendig, um diese Zahl im Rechner zu speichern? Begründen Sie Ihre Antwort.

*Lösung:*
Die maximale Zahl, die sich mit n-Bit darstellen lässt ist 2^n. Insofern benötigt man zur Darstellung der Zahl 10^78 ln(10^78) = 260 Bit, da log_10(2^260) = 78,268 ist.

## 2.3 Umwandlung zwischen Zahlensystemen (Ganzzahlen)
Vervollständigen Sie die leeren Felder:

|  Dezimal |     Binär |  Oktal |  Hexadezimal |
|----------|-----------|--------|--------------|
|  198     |           |        |              |
|          |  10101101 |        |              |
|          |           |   535  |              |
|          |           |        |  4AC         |

*Lösung:*

|  Dezimal |        Binär |  Oktal |  Hexadezimal |
|----------|--------------|--------|--------------|
| 198      | 11000110     |    306 |           C6 |
| 173      | 10101101     |    255 |           AD |
| 349      | 101011101    |    535 |          15D |
| 1196     | 10010101100  |   2254 |          4AC |

## 2.4 Umwandlung zwischen Zahlensystemen (Bruchzahlen)
Vervollständigen Sie die leeren Felder:

|  Dezimal |  Binär    |  Oktal |  Hexadezimal |
|----------|-----------|--------|--------------|
|  521,125 |           |        |              |
|          |  1011,11  |        |              |
|          |           |   15,7 |              |
|          |           |        |  AC,8        |

*Lösung:*

|   Dezimal |            Binär |   Oktal |   Hexadezimal |
|-----------|-----------------|---------|---------------|
|  521,125  |  1000001001,001 |  1011,1 |  209,2        |
|   11,750  |        1011,110 |    13,6 |    B,C        |
|   13,875  |        1101,111 |    15,7 |    D,E        |
|  172,500  |    10101100,100 |   254,4 |   AC,8        |

## 2.5 Gleitkommazahlen nach IEEE
Während der Fehlersuche stoßen Sie auf das folgende Speicherabbild:

`C0 98 00 00 00 00 00 00`

Welche Werte werden dargestellt, wenn Sie die Werte

1. als zwei IEEE-Gleitkommazahlen einfacher Genauigkeit bzw.
2. als eine IEEE-Gleitkommazahl doppelter Genauigkeit interpretieren?

Nehmen Sie für Ihre Betrachtung an, dass die Bytes in natürlicher Reihenfolge im Speicher abgelegt sind (Big-Endian-Format).

*Lösung:*
Eine 32-Bit IEEE-Gleitkommazahl hat folgenden Aufbau:

  * Bit 31: Vorzeichen (1 Bit)
  * Bit 30-23: Exponent (8 Bit)
  * Bit 22-0: Mantisse (23 Bit)

Der Bias beträgt 127

Zahl 1:

Die Zahl `C0 98 00 00` ist binär `11000000100110000000000000000000`

```console
1 10000001 00110000000000000000000
^ Exponent Mantisse
Vorzeichen
```

Damit ist
z = (-1)^1·1,0011·2^(129-127) = -1·100,11 = -1·(4 + 1/2 + 1/4)
  = -4,75

Zahl 2:
0000 0000 0000 0000 0000 0000 0000 0000
z=(-1)^0·0,0=0

Eine IEEE-Gleitkommazahl doppelter Genauigkeit:

  * Bit 64: Vorzeichen (1 Bit)
  * Bit 63-52: Exponent (11 Bit)
  * Bit 51-0: Mantisse (52 Bit)

Der Bias beträgt 1023

`C0 98 00 00 00 00 00 00` ist binär `1100000010011000000000000000000000000000000000000000000000000000`

```console
1 10000001001 1000000000000000000000000000000000000000000000000000
^ Exponent    Mantisse
Vorzeichen
```

z = (-1)^1·1,1·2^(1033-1023) = (-1)^1·11000000000 = -1536

## 2.6 Zweierkomplement
Wandeln Sie die Dezimalzahl -126 in eine binäre Darstellung mit 8 Bit um. Verwenden Sie die Zweierkomplementdarstellung für die Zahl.
*Lösung:*
126 = 1111110 binär

```console
 1111110
10000001 Bits invertieren
10000010 + 1
========
10000010
```

## 2.7 Zweierkomplement
Wandeln Sie die Dezimalzahl -1 in eine binäre Darstellung mit 8 Bit um. Verwenden Sie die Zweierkomplementdarstellung für die Zahl.
*Lösung:*
1 = 1 binär

```console
       1
11111110 Bits invertieren
11111111 + 1
========
11111111
```

## 2.8 Zweierkomplement
Wandeln Sie die Dezimalzahl -77 in eine binäre Darstellung mit 8 Bit um. Verwenden Sie die Zweierkomplementdarstellung für die Zahl.
*Lösung:*
77 = 1001101 binär

```console
 1001101
10110010 Bits invertieren
10110011 + 1
========
10110011
```

## 2.9 Sinn des Zweierkomplements
Warum ist es sinnvoll, einen Wert im Zweierkomplement darzustellen, bzw. worin liegt der Vorteil zur Darstellung im Einerkomplement?

*Lösung:*
Beide Darstellungsweisen dienen zur Codierung von vorzeichenbehafteten Zahlenwerten. In beiden Darstellungsweisen wird das Vorzeichen durch das führende Bit, das MSB, festgelegt. Eine führende 0 ist als +, eine führende 1 als - festgelegt. In der Einerkomplementdarstellung muss bei negativen Werten eine bitweise Invertierung des Betragswert erfolgen. Die Zweierkomplementdarstellung benötigt ebenfalls bei negativen Zahlen eine bitweise Invertierung. Hier wird nach der Invertierung zusätzlich eine Addition mit 1 durchgeführt. Der Wert einer Bitfolge in Zweierkomplementdarstellung ergibt sich immer als Summe der Einzelwertigkeiten, wobei hier auch der Wert des Vorzeichenbits als negativer Summand zur Berechnung genutzt wird.

## 2.10 Rechnen im Binärsystem
Führen Sie die folgenden binären Rechenoperationen durch

  * `110101 + 11001 =`
  * `111011 + 11101 =`
  * `111011 - 10111 =` (mit Zweierkomplement)
  * `110001 - 1101101 =` (mit Zweierkomplement)
  * `11011 * 1011 =`
  * `101,1101 + 1110,11 =`
  * `110,1001 - 101,11011 =`

*Lösung:*
```console
  110101   53       111011   59        0010111   23
+  11001   25      + 11101   29        1101001  (Zweierkomplement)
-------------      ------------      + 0111011   59
 1001110   78      1011000   88       -------------
                                    (1)0100100   36

 01101101  109
 10010011  (Zweierkomplement)
+  110001   49
--------------
 11000100  -60 (im Zweierkomplement)


 11011 * 1011  27 * 11 = 297
 ------------
 11011
   11011
    11011
 ------------
100101001


    101,1101    5,8125            110,10010    6,56250
 + 1110,11     14,7500          - 101,11011    5,84375
 ---------------------          ----------------------
 101000,1001   20,5625            000,10111    0,71875
```

## 2.11 Rechnen im Binärsystem - Addition
Bitte berechnen Sie binär, ohne in ein anderes Zahlensystem umzuwandeln: `110101 + 11001`

*Lösung:*
```console
    110101    53
+    11001    25
-----------------
   1001110    78
```

## 2.12 Rechnen im Binärsystem - Addition
Bitte berechnen Sie binär, ohne in ein anderes Zahlensystem umzuwandeln: `111011 + 11101`

*Lösung:*
```console
    111011    59
+    11101    29
-----------------
   1011000    88
```

## 2.13 Rechnen im Binärsystem - Subtraktion
Bitte berechnen Sie binär, ohne in ein anderes Zahlensystem umzuwandeln: `111011 - 10111` (mit Zweierkomplement)
*Lösung:*
```console
     10111    23
  11101001   (Zweierkomplement -23)
+   111011    59
-----------------
  100100100    36
```

## 2.14 Rechnen im Binärsystem - Subtraktion
Bitte berechnen Sie binär, ohne in ein anderes Zahlensystem umzuwandeln: `110001 - 1101101` (mit Zweierkomplement)
*Lösung:*
```console
   1101101   109
  10010011   (Zweierkomplement -109)
+   110001    49
-----------------
  11000100   -60
```

## 2.15 Bild codieren
Überlegen Sie sich ein Schema, wie das folgende Bild in Bits umgewandelt werden kann. Versuchen Sie die Daten so kompakt wie möglich abzulegen.

![](img/mario.png)

Codieren Sie die erste und die letzte Zeile nach Ihrem Schema und geben Sie das Ergebnis an. Gruppieren Sie dabei die Bits in Bytes.

*Lösung:*
weiß = 00
rot = 01
braun = 10
hellrot = 11

```console
1. Zeile:  00 00 00 00 00 01 01 01 01 01 00 00 00 00 00 00
16. Zeile: 00 00 01 01 01 01 00 00 00 00 01 01 01 01 00 00

1. Zeile:  00000000 00010101 01010000 00000000 = 0x00 0x15 0x50 0x00
16. Zeile: 00000101 01010000 00000101 01010000 = 0x05 0x50 0x05 0x50
```

## 2.16 Text codieren
Codieren Sie den folgenden Text in ISO-8859-1 und UTF-8.

"Mögest du viel Spaß haben!"

Geben Sie das Ergebnis als Bytes in hexadezimaler Schreibweise an.

*Lösung:*
ISO-8859-1:
4d f6 67 65 73 74 20 64 75 20 76 69 65 6c 20 53 70 61 df 20 68 61 62 65 6e 21 

UTF-8:
4d c3 b6 67 65 73 74 20 64 75 20 76 69 65 6c 20 53 70 61 c3 9f 20 68 61 62 65 6e 21 

UCS2:
4d 00 f6 00 67 00 65 00 73 00 74 00 20 00 64 00 75 00 20 00 76 00 69 00 65 00 6c 00 20 00 53 00 70 00 61 00 df 00 20 00 68 00 61 00 62 00 65 00 6e 00 21 00 

## 2.17 Sampling-Rate
Warum haben CDs eine Abtastrate von 44,1 kHz?

*Lösung:*
Der menschliche Hörsinn geht von 16 Hz bis ca. 19 kHz. Bei einer Abtastrate von 44,1 kHz kann man gemäß Nyquist-Shannon-Abtasttheorem Frequenzen bis 22 kHz aufnehmen. Eine höhere Abtastrate würde es erlauben, höhere Frequenzen aufzuzeichnen, diese könnten aber nicht wahrgenommen werden und würden nur die Datenmenge vergrößern.

## 2.18 Datenmenge einer CD
Eine CD zeichnet Audiosignale mit 16 Bit bei 44,1 kHz Abtastrate unkomprimiert auf. Wie groß wird eine Stereo-CD mit 70 Minuten Laufzeit ungefähr? Begründen Sie Ihre Antwort.

*Lösung:*
Bei 44,1 kHz werden alle 44.100 * 2 Byte pro Sekunde erzeugt. Das sind 86 kB pro Sekunde oder 5 MB pro Minute. 70 Minuten ergeben damit 350 MB pro Stereo-Kanal oder 700 MB in Summe für ein Stereo-Signal.

## 2.19 Umrechnung von Speicherkapazitäten
Eine Festplatte ist mit einer Speicherkapazität von 4 TB angegeben. Wieviele Bytes können Sie darauf speichern? Begründen Sie Ihre Antwort.

*Lösung:*
Festplattenhersteller verwenden Zehnerpotenzen für die Größenangaben, damit die Platten größer erscheinen. 4 TB = 4 * 10^12 Byte. 4 * 10^2 / 2^40 = 3,64 TiB

