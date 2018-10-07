# VideoSetup für das Chaotikum

Das VideoSetup im Space befindet sich noch im Aufbau. Aktuell sind noch nicht
alle Elemente vorhanden. Einige sind Leihgaben.

_Außerdem ist gitlab blöd und in wirklichkeit ist das Diagram viel bunter und
besser._


```mermaid
graph LR
  A[Presenter] -.-|Klinke| soundcard(USB-Soundkarte)
  A[Presenter] -->|HDMI| switch1>Switch 1]
  mic(Speaker Mic) ===|USB| usbHub
  cam1(FRONT CAM) -->|HDMI| switch1
  free1(Free) -->|HDMI| switch1
  switch1 -->|HDMI| elgato(Elgato)
  elgato -->|HDMI| switch2>Switch 2]
  elgato ===|USB 3| vLap[Video Laptop]
  vLap -->|HDMI| switch1
  switch2 -->|HDMI| hdmiaudiosplit1(HDMI/Audio-Splitter)
  hdmiaudiosplit1 -->|HDMI| beamer(Beamer)
  soundcard ===|USB| usbHub(USB 2.0 HUB)
  usbHub ===|USB| vLap
  webCam(WebCam) ===|USB| usbHub
  vLap ===|USB 3| coverter(Converter)
  coverter -->|HDMI| cam2(CAM)
  vLap -->|HDMI| splitter(Splitter)
  splitter -->|HDMI| switch1
  splitter -->|HDMI| switch3>Switch3]
  switch3 -->|HDMI| monitor1(Monitor)
  dashbordPi(Dashboard Pi) -->|HDMI| switch3
  funkempf1(Funk-Empfänger 1) -.-|Klinke| soundcard
  funkempf2(Funk-Empfänger 2) -.-|Klinke| soundcard
  cromecast((Crome Cast)) -->|HDMI| switch2
  free2(Free) -->|HDMI| switch2
  free3(Free) -->|HDMI| switch2
  funkmikro1(Funkmikro 1)
  funkmikro2(Funkmikro 2)
  hdmiaudiosplit1 -.-|Klinke| speaker(Lautsprecher)

  classDef Elgato fill:#efefef,stroke:#000,stroke-width:1px;
  classDef Switch fill:#ffaa11,stroke:#000,stroke-width:1px;
  classDef SoundCard fill:#eeff00,stroke:#000,stroke-width:1px;
  classDef HDMIAudiosplitter fill:#eeff00:stroke:#000,stroke-width:1px;
  classDef Beamer fill:#ee00aa,stroke:#000,stroke-width:1px;
  classDef Mic fill:#ADD8E6,stroke:#000,stroke-width:1px;
  classDef Converter fill:#efefef,stroke:#000,stroke-width:1px;
  classDef Pi fill:#8A2BE2,stroke:#000,stroke-width:1px;
  classDef Free fill:#FFFFFF,stroke:#FFFFFF,stroke-width:1px;
  classDef CromeCast fill:#ffaaff,stroke:#FFFFFF,stroke-width:1px;
  classDef FunkMikro fill:#00ff00,stroke:#FFFFFF,stroke-width:1px;

  classDef NotPresent stroke:#ff0000,stroke-width:3px;

  class A cssClass;
  class elgato Elgato;
  class switch1 Switch;
  class switch2 Switch;
  class switch3 Switch;
  class soundcard SoundCard;
  class hdmiaudiosplit1 HDMIAudiosplitter;
  class beamer Beamer;
  class mic Mic;
  class coverter Converter;
  class dashbordPi Pi;
  class free1 Free;
  class free2 Free;
  class free3 Free;
  class cromecast CromeCast;
  class funkmikro1 FunkMikro;
  class funkmikro2 FunkMikro;
  class funkempf1 FunkMikro;
  class funkempf2 FunkMikro;

  class hdmiaudiosplit1 NotPresent;
  class cam1 NotPresent;
  class beamer NotPresent;
  class soundcard NotPresent;
  class mic NotPresent;
  class switch3 NotPresent;
  class hdmiaudiosplit1 NotPresent;

  linkStyle 7 stroke:#0000ff,stroke-width:2px;
  linkStyle 14 stroke:#0000ff,stroke-width:2px;
```

   * **Presenter:** Ist der Laptop des Präsentierenden. *HDMI* steht zur
   Verfügung. *Klinke* ist langfristig angedacht. *VGA* vielleicht auch mal,
   lieber nur per Adapter.
   * **Switch1:** Ist ein mechanischer HDMI-Switch, in welchen die HDMI Ports
   gehen, welche in den Elgato gehen.
   * **Elgato:** Elgato greift das eingehende *HDMI* Signal ab und schickt es
   per USB 3.0 an den Video-Laptop.
   * **Switch2:** Einige Geräte können nicht durch den Elgato abgegriffen
   werden, da DRM-Dinge dies verhindern, diese können hier in den mechsnischen
   Switch eingehängt werden.
   * **HDMI/Audio-Splitter** Damit das Audio-Signal auf die Lautsprecher und
   nicht (nur) auf den beamer geht, wird es hier abgegriffen.
   * **Beamer:** Der Beamer ist halt der Beamer.
   * **Chrome Cast:** Google Chrome Cast.
   * **Switch3:** Der mechanische Switch entscheidet, welcher HDMI-Input auf den Monitor
   im hinteren Raumbereich
   * **Monitor:** Der Monitor hinten am Regal. DVI in.
   * **Front Cam:** Ein Camcorder, der sein Signal per HDMI ausgiebt, kann
   anstelle des Inputs vom Laptop angezeigt werden.**AKTUELL EXISTIERT DIESE
   KAMERA NOCH NICHT**
   * ...

## Belegung der Switches

### Switch 1

```mermaid
graph LR
  in1[Presenter Laptop] -->|Input 1| switch1>Switch 1]
  in2[Video Laptop] -->|Input 2| switch1
  in3[Front Cam] -->|Input 3| switch1
  in4[Frei] -->|Input 4| switch1
  switch1 -->|Output| elgato(Elgato)
```

### Switch 2

```mermaid
graph LR
  in1(Elgato) -->|Input 1| switch2>Switch 2]
  in2((Chrome Cast)) -->|Input 2| switch2
  in3[Frei] -->|Input 3| switch2
  in4[Frei] -->|Input 4| switch2
  switch2 -->|Output| beamer(HDMI/Audio-Switch bzw. Beamer)
```

### Switch 3

```mermaid
graph LR
  in1(Dashboard Pi) -->|Input 1| switch3>Switch 3]
  in2[Video Laptop] -->|Input 2| switch3
  in3[Frei] -->|Input 3| switch3
  in4[Frei] -->|Input 4| switch3
  switch3 -->|Output| monitor(Monitor)
```
