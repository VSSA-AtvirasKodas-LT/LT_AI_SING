# LT_AI_SING

### Turinys
- [LT\_AI\_SING](#lt_ai_sing)
    - [Turinys](#turinys)
  - [Apie](#apie)
  - [Garsynas](#garsynas)
  - [Šnekos sintezė](#šnekos-sintezė)
    - [Pavyzdžiai](#pavyzdžiai)
    - [Paruošti modeliai](#paruošti-modeliai)
      - [Vyriškas balsas](#vyriškas-balsas)
      - [Moteriškas balsas](#moteriškas-balsas)
    - [Demonstracija internete](#demonstracija-internete)
      - [Lokalioje mašinoje](#lokalioje-mašinoje)
    - [Modelių mokymo skriptai](#modelių-mokymo-skriptai)
 
## Apie

LT_AI_SING repozitorija skirta pademonstruoti, kaip Sintezės Garsyno (SING) balso įrašai gali būti naudojami lietuvių kalbos sintezei.

## Garsynas

Pilnas garsyno aprašymas: *TDB nuoroda...*

Garsyną sudaro 20 balsų. Bendra garsyno apimtis yra 200 val. *TDB...*

Garsyno parsisiuntimo nuoroda: *TDB...*

## Šnekos sintezė

Demonstracijai sukurti modeliai dviem balsams: vyriškam ir moteriškam. Jie patalpinti [HuggingFace](https://huggingface.co/VSSA-SDSA) modelių saugykloje. Modelių mokymui ir sintezavimo demonstracijai naudojami atvirojo kodo [ESPnet](https://espnet.github.io/espnet/) ir [ParallelWaveGAN](https://github.com/kan-bayashi/ParallelWaveGAN) įrankiai.


### Pavyzdžiai
|Balsas|Lytis|Tipas|Audio|
|-|-|-|-|
|ARN|vyriškas|FastSpeech2 + Style MelGAN| [audio](./samples/arn01.mp3) |
|||| [audio](./samples/arn02.mp3) |
|AGN|moteriškas|FastSpeech2 + Style MelGAN| [audio](./samples/agn01.mp3) |
|||| [audio](./samples/agn02.mp3) |

### Paruošti modeliai 

Šnekamosios kalbos sintezatoriaus sprendimas vienam balsui sintezuoti naudoja du išmoktus modelius: akustinį modelį ir vokoderį.

#### Vyriškas balsas

1. Akustinis modelis: [VSSA-SDSA/sing-arn.fastspeech2.v01](https://huggingface.co/VSSA-SDSA/sing-arn.fastspeech2.v01)
2. Vokoderis: [VSSA-SDSA/sing-arn.vocoder.style_melgan.v01](https://huggingface.co/VSSA-SDSA/sing-arn.vocoder.style_melgan.v01)

#### Moteriškas balsas

3. Akustinis modelis: [VSSA-SDSA/sing-agn.fastspeech2.v01](https://huggingface.co/VSSA-SDSA/sing-agn.fastspeech2.v01)
4. Vokoderis: [VSSA-SDSA/sing-agn.vocoder.style_melgan.v01](https://huggingface.co/VSSA-SDSA/sing-agn.vocoder.style_melgan.v01) 


### Demonstracinio sintezės sprendimo vartotojo instrukcija

Čia galite rasti pažingsninę techninę vartotojo instrukciją (Jupyter failą), kuri demonstruoja kaip šnekos sintezei panaudoti HuggingFace repozitorijoje patalpintus demonstracinius sintezavimo modelius: [notebooks/tts_demo.ipynb](notebooks/tts_demo.ipynb).

Demonstracinio failo nuoroda internete: [![Atidaryti Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/VSSA-AtvirasKodas-LT/LT_AI_SING/blob/main/notebooks/tts_demo.ipynb)


#### Demonstracinio sintezės sprendimo administratoriaus instrukcija

Čia galite rasti pažingsninę techninę administratoriaus [instrukciją](notebooks/tts_demo_local.ipynb) (Jupyter failą), kuris demonstruoja, kaip vietiniame kompiuteryje Python aplinkoje galima sintezuoti lietuvišką šneką. Jums reikia:
1. Susidiegti [ESPnet paketą](https://github.com/airenas/espnet/blob/master/egs2/sing/tts1/README.lt.md#espnet-diegimas).
2. Papildomai ESPnet conda aplinkoje įdiekite vokoderio kodą ir Jupyter: `pip install parallel_wavegan jupyter --no-build-isolation`.
3. Parsisiųskite modelius iš [Paruošti modeliai](#paruošti-modeliai) arba naudokite savo apmokytus. Pvz., modelius parsisiųsti galima su `git` komanda (reikia papildomai įsidiegti `git-lfs`): `git clone https://huggingface.co/VSSA-SDSA/sing-agn.fastspeech2.v01`
4. Paleiskite Jupyter Notebook ir naršyklėje atsidarykite failą [notebooks/tts_demo_local.ipynb](notebooks/tts_demo_local.ipynb). Sekite instrukcijas Jupyter faile.


### Demonstracinio sintezės sprendimo techninis aprašas, mokymo ir diegimo instrukcijos

Čia galite rasti techninį aprašą ir nuorodas į GitHub repozitorijas, kuriose pateiktos pažingsninės instrukcijos, kaip išmokyti akustinį modelį ir vokoderį, naudojantis SING garsyno diktorių balso duomenimis:

- Akustinio modelio mokymo skriptai ir instrukcija: [ESPnet](https://github.com/airenas/espnet/blob/master/egs2/sing/tts1/README.lt.md).
- Vokoderio mokymo skriptai ir instrukcija: [ParallelWaveGAN](https://github.com/airenas/ParallelWaveGAN/blob/master/egs/sing/voc1/README.lt.md).

