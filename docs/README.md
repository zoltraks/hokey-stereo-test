
# ```HOKEY BASIC STEREO TEST```

# Introduction

The [POKEY](https://en.wikipedia.org/wiki/POKEY) sound chip was used in the ATARI family of 8-bit computers.

The 5200 console also contains it, while the 2600 and 7800 consoles do not contain the POKEY chip.

In the case of the 7800 console, the POKEY chip was placed on the cartridge along with the game to enable sound playback.

For 7800 there is possiblity to use multicart Concerto which uses SD card reader and allows to play most of the games on 7800 console.

However it needs POKEY chip to be mounted.

Also popular STEREO extension needs second POKEY to be mounted in ATARI machine.

An alternative to the increasingly hard-to-find POKEY chip is the FPGA based PokeyMax chip.

It provides a different set of configurations (STEREO, QUAD, COVOX, SID, YM). Unfortunatelly is currently difficult to obtain these days.

A replacement for the POKEY system dedicated for use in the Concerto called HOKEY has recently become available.

Here is a description from the producer of Concerto and HOKEY chips, [Atari Age](https://atariage.com/) forum user [batari](https://forums.atariage.com/profile/5792-batari/).


```
HOKEY was intended as a POKEY replacement for Atari 7800 homebrews but has evolved into a low-cost sound chip for Atari 7800 games. It is the only POKEY replacement with a form factor that is essentially the same as a real POKEY. It's also the lowest-cost POKEY replacement chip by a wide margin.
```

```
HOKEY's implementation of POKEY is based on the public domain datasheet and schematics of POKEY. It's a completely original POKEY implementation without use of any existing source code. HOKEY is intended as a functional replication of POKEY sound capabilities and was never intended to be a 100% authentic reproduction of the chip at the gate level. However, I will make every effort to ensure HOKEY can faithfully produce the various distortions. 
```

The cheapest option is to use the basic version of the HOKEY chip. This variant only contains the audio generation functionality of the POKEY chip.

It cannot therefore be used instead of the original chip, but it can be used as a second chip in the STEREO extension.

It should be noted that HOKEY is dedicated for use by multicards.

This document contains the results of testing the use of the HOKEY basic chip as a second sound chip for STEREO extension in PAL machine.

## Credits

|||
|-|-|
|Filip Golewski|**ZoltarX**|
|Vin Samuel|**VinsCool**|
|Grzegorz Żyła|**SuN**|

## Test kit

<div style="max-width: 900px">

![](../media/TEST%20KIT%201.jpg)

</div>

 - **HOKEY Basic** x 2

 - **POKEY** x 3

 - **PokeyMax v2** with STEREO configuration

 - **SimpleStereo v2** STEREO board

 - **Altirra** emulator

 - **ATARI 130 XE PAL** machine

 - **Focusrite Scarlett 2i2** audio interface

All recordings were made in 24-bit resolution at 48kHz.

Source WAV files size is almost 7 GB.

## Test configurations

``POKEY + HOKEY``

POKEY plays on the left channel.

HOKEY plays on the right channel. 

<div style="width: 300px">

![](../media/CONFIGURATION%20POKEY%20%2B%20HOKEY.jpg)

</div>

``POKEY + POKEY``

Standard STEREO configuration.

<div style="width: 300px">

![](../media/CONFIGURATION%20POKEY%20%2B%20POKEY.jpg)

</div>

``PokeyMax v2``

FPGA replacement for two POKEY configuration (SC firmware). 

<div style="width: 300px">

![](../media/CONFIGURATION%20MAX.jpg)

</div>

# Preparations

## Levels

Output levels of both chips are different.

HOKEY output level is -10dB quieter than original POKEY chip.

![](../media/HOKEY%20ZERO%20LEVEL.png)

It can be compesated with 140 Ω resistor between channel audio out and audio ground.

![](../media/EDA%20COMPENSATION.png)

However most of the recordings were made without any additional electrical elements.

## Adjustments

PokeyMax documentation recommends use of polarized 10 μF capacitors at audio output.

![](../media/EDA%20CAPACITOR%20POLARIZED.png)

![](../media/MAX%20SCHEMATICS.png)

In first configuration bipolarized audio capacitors were used.

![](../media/EDA%20CAPACITOR.png)

![](../media/PHOTO%20CAPACITOR.png)

## Checks

**CHECK 0** is pure tone check. Uses distortion $A.

[CHECK 0.rmt](../download/CHECK%200.rmt)

[CHECK 0.xex](../download/CHECK%200.xex)

**CHECK 1** is melody test. Uses various timbres.

[CHECK 1.rmt](../download/CHECK%201.rmt)

[CHECK 1.xex](../download/CHECK%201.xex)

**CHECK 2** uses note A with different volume levels. Playing similar frequencies results in wave interferences.

[CHECK 2.rmt](../download/CHECK%202.rmt)

[CHECK 2.xex](../download/CHECK%202.xex)

**CHECK 3** contains frequency check using all distortions but pure tone.

[CHECK 3.rmt](../download/CHECK%203.rmt)

[CHECK 3.xex](../download/CHECK%203.xex)

**CHECK 4** ia s special check that uses volume only mode to generate sound. 

[CHECK 4.rmt](../download/CHECK%204.rmt)

[CHECK 4.xex](../download/CHECK%204.xex)

**CHECK 5** uses 1/2 and 3/4 generators to determine differences in phase shift. 

[CHECK 5.rmt](../download/CHECK%205.rmt)

[CHECK 5.xex](../download/CHECK%205.xex)

**CHECK 6** is a pure tone test using two lowest sounds $FF and $FE in 64 kHz mode played on both sound chips to find the proper tuning. 

[CHECK 6.rmt](../download/CHECK%206.rmt)

[CHECK 6.xex](../download/CHECK%206.xex)

**CHECK FE** is similar test using two lowest sounds $FF and $FE in 64 kHz mode played on each generator. 

[CHECK FE.rmt](../download/CHECK%20FE.rmt)

[CHECK FE.xex](../download/CHECK%20FE.xex)

**CHECK FD** is using $FF and $FD in 64 kHz mode to find the proper tuning. 

[CHECK FD.rmt](../download/CHECK%20FD.rmt)

[CHECK FD.xex](../download/CHECK%20FD.xex)

**CHECK FC** is using $FF and $FC in 64 kHz mode. 

[CHECK FC.rmt](../download/CHECK%20FC.rmt)

[CHECK FC.xex](../download/CHECK%20FC.xex)

**CHECK AF** tests frequency differences for division values +1 / -1 for notes in range C-3 to B-5. 

[CHECK AF.rmt](../download/CHECK%20AF.rmt)

[CHECK AF.xex](../download/CHECK%20AF.xex)

# Tests

## Scenarios

**HOKEY 1** tests were made with POKEY '87 and one of HOKEY basic chip without electrical level adjustment.

**HOKEY 2** tests were made with POKEY '87 and second of HOKEY basic chip using 140 Ω resitor for level adjustment.

**POKEY 1** tests were made with POKEY '87 and '82 POKEY chip.

**POKEY 2** tests were made with POKEY '87 and '85 POKEY chip.

**MAX 1** tests were made with PokeyMax with capactitors.

**MAX 2** tests were made with PokeyMax without capactitors.

### ``CHECK 0``

![](../media/ALL%20CHECK%200%20OVERVIEW.png)

![](../media/ALL%20CHECK%200%20FRAGMENT.png)

This test is intended to show the differences in the sound of the system for a single tone played on individual generators at minimum and maximum volume for pure tone and white noise.

In this test, the distortion used was $A (pure tone) for the A note at different octaves and $8 (white noise) played at the maximum available frequency (minimum divider value).

|||
|-|-|
| A<sub>4</sub> | Volume level $F, single channel 1, 2, 3, 4 |
| A<sub>4</sub> | Volume level $1, single channel 1, 2, 3, 4 |
| A<sub>3</sub> + A<sub>4</sub> + A<sub>5</sub> + A<sub>6</sub> | Volume levels $FFFF, $FEDC, $F842, $248F, all channels |
| $03, $02, $01, $00 | Volume level $F, single channel, different division values |
| $00 + $01 + $02 + $03 | Volume levels $FFFF, $FEDC, $F842, $248F, all channels |
| A<sub>1</sub> + A<sub>2</sub> + A<sub>3</sub> + A<sub>4</sub> (15 kHz) | Volume level $F, single channel 1, 2, 3, 4 |

![](../media/RMT%20CHECK%200%20A.png)

### ``CHECK 1``
---

![](../media/ALL%20CHECK%201%20OVERVIEW.png)

![](../media/ALL%20CHECK%201%20FRAGMENT.png)

This check contains several short music patterns using different kind of instruments played once on the left and another on the right channel.

![](../media/RMT%20CHECK%201%20A.png)

### ``CHECK 2``
---

![](../media/ALL%20CHECK%202%20OVERVIEW.png)

![](../media/ALL%20CHECK%202%20FRAGMENT.png)

This test uses the note A for different volumes using the beat effect resulting from the overlap of successive sounds with similar frequencies in following passes.

![](../media/RMT%20CHECK%202.png)

### ``CHECK 3``
---

![](../media/ALL%20CHECK%203%20OVERVIEW.png)

![](../media/ALL%20CHECK%203%20FRAGMENT.png)

In this test noise ($0, $8) and bass distortions ($2, $C, $E) will be tested from the lowest possible notes until maximum. 

![](../media/RMT%20CHECK%203.png)

### ``CHECK 4``
---

![](../media/ALL%20CHECK%204%20OVERVIEW.png)

![](../media/ALL%20CHECK%204%20FRAGMENT.png)

Volume only test. Sound is made by quickly (8 per frame) change sound from minimum to maximum. This results in a waveform at frequency at about 130.9 Hz.

During the play, volume is increased from minimum to maximum.

![](../media/RMT%20CHECK%204%20A.png)

![](../media/RMT%20CHECK%204%20B.png)

### ``CHECK 5``
---

![](../media/ALL%20CHECK%205%20OVERVIEW.png)

![](../media/ALL%20CHECK%205%20FRAGMENT.png)

Playing sound on the lowest and highest possible divisor values for pure tone ``$A`` and noise ``$8`` distortions.

Notes are played once on first channel, then on third to check difference between 1/2 and 3/4 sound generators as they are supposed to play in different phases.

Simple music using possible interferences between 2nd and 4th channel is played at the end.

![](../media/RMT%20CHECK%205%20A.png)

![](../media/RMT%20CHECK%205%20B.png)

## Songs
---

|||||
| -------------------- |-|-|-|
| "Second Life Syndrome" | VLX/Lamers | SLS | 6:09
| "Surprise" | XTD/Lamers | SURPRISE | 2:02
| "5th Generation" | XTD/Lamers | 5TH GENERATION  | 3:42
| "Unified Theme Remix" | New Generation | UTR | 3:19
| "Midnight Rider" | PG | MIDNIGHT RIDER | 3:07
| "Unmec" | stRing/Agenda | UNMEC | 4:04
| "The Hall of Rabarbadon" | Miker/Slight | HALL OF RABARBADON | 2:36
| "Precel Kopernika" | ZoltarX/NG | PRECEL KOPERNIKA | 3:20
| "WHO DIS" | ZoltarX/NG | WHO DIS | 2:36
| "AC23INV" | ZoltarX/NG | AC23INV | 2:58

Music is played by both POKEY and HOKEY chips.

POKEY plays on left channel (top) while HOKEY plays on right channel (bottom).

![](../media/POKEY%20%2B%20HOKEY.png)

# Results

## Bugs

Pure tone generated by HOKEY contains some glitches in its envelope.

![](../media/GLITCH%20PURE%20TONE%201.png)

![](../media/GLITCH%20PURE%20TONE%202.png)

Sometimes when volume level goes to zero, HOKEY starts to play strange noise.

It's quiet but can be easily heard when nothing else is played.

![](../media/HOKEY%20BUG%201.png)

Sometimes it freezes and sticks with more louder weird sounds.

Cold reboot is needed.

![](../media/HOKEY%20BUG%202.png)

![](../media/HOKEY%20BUG%204.png)

## Checks

### ```CHECK 0```
---

This test shows a smoother wave envelope generated by HOKEY.

![](../media/RMT%20CHECK%200%20B.png)

Spectrum for POKEY shows peak value at 440Hz which seems to be correct value to desired 439.84 Hz for PAL.

<div style="width: 350px">

![](../media/PLOT%20PURE%20TONE%201%20POKEY.png)

</div>

HOKEY in this case is more close to 450Hz.

<div style="width: 400px">

![](../media/PLOT%20PURE%20TONE%201%20HOKEY.png)

</div>

Let's look at pitch values for different period multiplier values. 

Test music uses value **$47** for note **A** with 64 kHz clock.

| Pitch | PAL | NTSC |
| - | - | - |
| $45 | 452.41 Hz | 456.57 Hz |
| $46 | 446.04 Hz | 450.14 Hz |
| **$47** | **439.84** Hz | **443.89** Hz |
| $48 | 433.82 Hz | 437.81 Hz |

The reason might be that HOKEY is internally tuned for NTSC mode and it's used in PAL machine. In NTSC mode frequency should be more like 443.89 kHz but because of slightly different CPU clock frequency, it is a bit higher. 

### ```CHECK 1```
---

As in the previous test, a softer wave envelope is observed.

![](../media/RMT%20CHECK%201%20B.png)

For this test, a spectrum analysis was performed for a fragment of a melody played alternately in the left and right channels.

![](../media/RMT%20CHECK%201%20SPECTRUM%20POKEY.png)

![](../media/RMT%20CHECK%201%20SPECTRUM%20HOKEY.png)

POKEY and HOKEY spectrum combined.

![](../media/RMT%20CHECK%201%20SPECTRUM%20POKEY%20%2B%20HOKEY.png)

After applying high pass filter at 8 kHz and normalization, spectrum analysis comparisation looks little different.

![](../media/RMT%20CHECK%201%20SPECTRUM%208kHz%20POKEY.png)

![](../media/RMT%20CHECK%201%20SPECTRUM%208kHz%20HOKEY.png)

POKEY and HOKEY spectrum combined.

![](../media/RMT%20CHECK%201%20SPECTRUM%208kHz%20POKEY%20%2B%20HOKEY.png)

### ```CHECK 2```
---

It looks like HOKEY can't play maximum available frequency for noise distortion $8. 

In the folowing diagram you can see first POKEY, HOKEY in the middle and second POKEY which correctly plays noise sound. 

![](../media/RMT%20CHECK%200%20C.png)

This is definetely a bug.

![](../media/RMT%20CHECK%200%20D.png)

### ```CHECK 4```
---

This test totally fails on HOKEY.

![](../media/RMT%20CHECK%204%20C.png)

It is almost perfect for MAX.

![](../media/MAX%201%20CHECK%204.png)

### ```CHECK 5```
---

![](../media/CHECK%205%20PHASE%20CHECK%201.png)

![](../media/CHECK%205%20PHASE%20CHECK%201.png)

Phase shift can be observed when playing the same notes betweek POKEY and HOKEY.

![](../media/CHECK%205%20PHASE%20DIFFERENCE%201.png)

![](../media/CHECK%205%20PHASE%20DIFFERENCE%201.png)

### ```CHECK AF```
---

![](../media/CHECK%20AF%20TUNE%201.png)

![](../media/CHECK%20AF%20TUNE%203.png)

![](../media/NOTE%20FREQUENCY%201.png)

[NOTE FREQUENCY.ods](../download/NOTE%20FREQUENCY.ods)

## Songs

Several songs played in STEREO mode.

HOKEY can be heard on right channel, while original POKEY plays on left.

<style>
.two-column-picture-table:after { content: ""; display: table; clear: both; }
.two-column-picture-table > div { float: left; width: 50%; }
</style>

## "Second Life Syndrome" by VLX/Lamers

[Download →](https://drive.google.com/file/d/1oLzJhXCg7r6u875XbtXcuhCaggu9U8_9/view?usp=share_link)

MONO module.

Both envelopes match.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20SLS%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%20SLS%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20SLS%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%20SLS%20SHOT%204.png)

</div>

</div>

<!-- -->

## "Surprise" by XTD/Lamers

[Download →](https://drive.google.com/file/d/1GAsIc_oa01K0qdISXvJ1iEmiERejMMpv/view?usp=share_link)

MONO module.

Both envelopes match.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%204.png)

</div>

</div>

<!-- -->

## "5th Generation" by XTD/Lamers

[Download →](https://drive.google.com/file/d/12D8Q5aLVl4WxWBipwutoWP_syd_DuY3O/view?usp=share_link)

STEREO module.

Envelopes don't match each other.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%205TH%20GENERATION%20SHOT%204.png)

</div>

</div>

<!-- -->

## "Unified Theme Remix" by New Generation

[Download →](https://drive.google.com/file/d/1P8YDEU-hX_6Qut94PpSyr9qarQhnpNMg/view?usp=share_link)

STEREO module.

Envelopes don't match each other.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20UTR%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%20UTR%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20UTR%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%20UTR%20SHOT%204.png)

</div>

</div>

<!-- -->

## "Midnight Rider" by PG

[Download →](https://drive.google.com/file/d/1YcVekk7BbwLLoOrGS4ScV2N6jY16eqP-/view?usp=share_link)

STEREO module.

Envelopes don't match each other.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20MIDNIGHT%20RIDER%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%20MIDNIGHT%20RIDER%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20MIDNIGHT%20RIDER%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%20MIDNIGHT%20RIDER%20SHOT%204.png)

</div>

</div>

<!-- -->

## "Unmec" by stRing/Agenda

[Download →](https://drive.google.com/file/d/1xeuMZT1YxzJTHV1ZkDbU-vaIuyfI52Fb/view?usp=share_link)

MONO module.

Both envelopes match.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20UNMEC%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%20UNMEC%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20UNMEC%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%20UNMEC%20SHOT%204.png)

</div>

</div>

<!-- -->

## "The Hall of Rabarbadon" by Miker/Slight

[Download →](https://drive.google.com/file/d/19uZWBKn9rG4lBUAkYXsVaTCwHWxHlK61/view?usp=share_link)

MONO module.

Both envelopes match.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%202%20HALL%20OF%20RABARBADON%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%202%20HALL%20OF%20RABARBADON%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%202%20HALL%20OF%20RABARBADON%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%202%20HALL%20OF%20RABARBADON%20SHOT%204.png)

</div>

</div>

<!-- -->

## "Precel Kopernika" by ZoltarX/NG

[Download →](https://drive.google.com/file/d/1JLakeBYe0qBmVRl0Zdw1Kksdo8uwpueZ/view?usp=share_link)

PSEUDO STEREO module.

Second envelope is delayed by 1 frame (20 ms). 

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20PRECEL%20KOPERNIKA%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%201%20PRECEL%20KOPERNIKA%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%201%20PRECEL%20KOPERNIKA%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%201%20PRECEL%20KOPERNIKA%20SHOT%204.png)

</div>

</div>

<!-- -->

## "WHO DIS" by ZoltarX/NG

[Download →](https://drive.google.com/file/d/13IBsgB0fdWhNCL-XGJdNmCXPUu7FJd1a/view?usp=share_link)

MONO module.

Both envelopes match.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%202%20WHO%20DIS%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%202%20WHO%20DIS%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%202%20WHO%20DIS%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%202%20WHO%20DIS%20SHOT%204.png)

</div>

</div>

<!-- -->

## "AC23INV" by ZoltarX/NG

[Download →](https://drive.google.com/file/d/167O8SlOsKBGXMCE6CqYu4I_j49m-3p2T/view?usp=share_link)

MONO module.

Both envelopes match.

### ```POKEY``` + ```HOKEY```

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%202%20AC23INV%20SHOT%201.png)

</div>

<div>

![](../media/HOKEY%202%20AC23INV%20SHOT%202.png)

</div>

</div>

<!-- -->

<div class="two-column-picture-table">

<div>

![](../media/HOKEY%202%20AC23INV%20SHOT%203.png)

</div>

<div>

![](../media/HOKEY%202%20AC23INV%20SHOT%204.png)

</div>

</div>

<!-- -->

# Conslusions

1) HOKEY plays too quietly, and not -6 dB, but rather -10 dB

2) HOKEY is out of tune because it is probably intended to be used in NTSC machine, which, when combined with a PAL machine, results in a frequency shift to slightly higher frequencies (450 Hz vs 440 Hz)

3) HOKEY tends to play in inverted phase

4) HOKEY does not play the highest noise frequencies (distortion $8, divisor $00)

5) HOKEY has errors in generating a clean tone (might be a result of point two)

# Downloads

Recordings are available to download in compressed OGG format made with the highest quality (q=10).

[Google Drive](https://drive.google.com/drive/folders/1wB2agwoQ7CWhYTWNTUjPmV-92VNQERBi?usp=share_link)

This quality is still enough to further analysis.

And we got 1/4 the size comparing to uncompressed data.

## Frequency tables

The following frequency tables were generated using the program ``RMT 1.34 2023-01-01``.

Frequency table for tone A, distortion $A (czyty ton) for 64 kHz audio clock.

| | POKEY (PAL) | POKEY (NTSC) | |
|-|-|-|-|
| A<sub>3</sub> | 219,92 Hz | 221,95 Hz | 220,00 Hz |
| A<sub>4</sub> | 439,84 Hz | 443,89 Hz | 440,00 Hz |
| A<sub>5</sub> | 879,69 Hz | 887,78 Hz | 880,00 Hz |
| A<sub>6</sub> | 1759,37 Hz | 1775,57 Hz | 1760,00 Hz |

Frequency table for tone A, distortion $A (czyty ton) for 15 kHz audio clock.

| | POKEY (PAL) | POKEY (NTSC) | |
|-|-|-|-|
| A<sub>3</sub> | 55,17 Hz | 55,67 Hz | 55,00 Hz |
| A<sub>4</sub> | 109,55 Hz | 110,56 Hz | 110,00 Hz |
| A<sub>5</sub> | 222,24 Hz | 224,28 Hz | 220,00 Hz |
| A<sub>6</sub> | 432,13 Hz | 436,10 Hz | 440,00 Hz |

Division table for noise, distortion $8 for 64kHz audio clock.


| | POKEY (PAL) | POKEY (NTSC) | |
|-|-|-|-|
| $00 | 31668,70 Hz | 31960,23 Hz |
| $01 | 15834,35 Hz | 15980,12 Hz |
| $02 | 10556,23 Hz | 10653,41 Hz |
| $03 | 7917,17 Hz | 7990,06 Hz |

## Reference materials

Frequency table for equal tempered tuning system.

https://pages.mtu.edu/~suits/notefreqs.html

Atari Age forum posts from the producer of Concerto and HOKEY.

https://forums.atariage.com/topic/314517-concerto-sd-card-multicart-ordering-info/

https://forums.atariage.com/topic/321741-hokey-demo/?do=findComment&comment=4968839

https://forums.atariage.com/topic/348255-dkr-wip/

https://forums.atariage.com/topic/346754-hokey-pokey-sound-issues/
