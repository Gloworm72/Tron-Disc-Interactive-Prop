# Tron Identity Disc Interactive Prop

[![Watch the Demo Video](https://img.youtube.com/vi/1LMHvsbs-kQ/0.jpg)](https://www.youtube.com/watch?v=1LMHvsbs-kQ)

---

A fully functional Tron Identity Disc built using a Proffieboard v2.2 and inspired by the weapon from *Tron: Legacy*. Features real-time motion-reactive lighting, synchronized sound effects, and a total of 15 customizable profiles.

This project was a personal passion project blending my love for themed entertainment, prop-making, and embedded systems.

---

## Features

- **Proffieboard v2.2** with fully custom configuration
- **Four separate LED segments** using high-density WS2812B NeoPixels (720+ LEDs total)
- **Dual speakers** for stereo sound output
- **Motion sensing** with clash, swing, and blaster deflection detection
- **Interactive lighting** using custom blade styles
- **3D printed housing** with detailed paintwork and weathering
- **Configurable via ProffieOS** and `config.h`

---

## Profiles

Switch between 15 unique sound/LED profiles with themed tracks and FX:

1. **Flynn** – The Son of Flynn  
2. **CLU** – Clu Song from Soundtrack  
3. **Rinzler** – Rinzler’s Pursuit  
4. **Rectify** – Recognizer / Control  
5. **Games** – Disc Wars Arena  
6. **Electrify** – Derezzed (Daft Punk)  
7. **Maggie** – Custom profile for friend  
8. **Irish** – Victory March  
9. **Cyber** – Fall  
10. **Masterless** – Encom II  
11. **Magnetic** – Nocturne  
12. **Decay** – Flynn Lives  
13. **Dark** – Mandalorian (Bonus FX)  
14. **Kylo** – Dual if the Fates FX Saber  
15. **Rave** – OIIA (Disco Blade Mode)

Each profile includes:
- Ignition / Retraction
- Clash, Lockup, and Blaster effects
- Background hum and looping music
- Custom LED animations synced with audio

---

## 🛠Build Process

**3D Print & Paint**  
- Designed in Fusion 360  
- Printed with PLA  
- Sanded, base coated, then layered with gloss acrylics and weathering techniques

**Electronics Assembly**  
- Wired all LED strips and speakers to the Proffieboard  
- Installed kill switch and recharge port  
- Routed wires through the disc frame and secured with heat shrink

**Software**  
- Configured 15 preset profiles in `config.h`  
- Uploaded using ProffieOS + Arduino IDE  
- Customized blade styles and sound effects for each track

**Testing**  
- Validated sensitivity of swing and clash detection  
- Synced audio and LED effects  
- Performed endurance and runtime checks

---

## Sample Proffie Config Snippet

```cpp
#define NUM_BLADES 4
#define NUM_BUTTONS 2
#define VOLUME 1500
const unsigned int maxLedsPerStrip = 720;

#ifdef CONFIG_PROP
#include "../props/saber_fett263_buttons.h"
#endif

Preset presets[] = {
   { "Flynn", "tracks/TheSonOfFlynn.wav",
	StylePtr<Layers<White,TransitionEffectL<TrConcat<TrInstant,AlphaL<Black,SmoothStep<Int<2048>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<4096>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<6144>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<8192>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<10240>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<12288>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<14336>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<16384>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<18432>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<20480>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<22528>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<24576>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<26624>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<28672>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<30720>,Int<0>>>,TrDelay<150>,AlphaL<Black,SmoothStep<Int<32768>,Int<0>>>,TrDelay<150>>,EFFECT_NEWFONT>,TransitionEffectL<TrConcat<TrInstant,AlphaL<Black,SmoothStep<Int<2048>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<4096>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<6144>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<8192>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<10240>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<12288>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<14336>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<16384>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<18432>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<20480>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<22528>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<24576>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<26624>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<28672>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<30720>,Int<0>>>,TrDelay<500>,AlphaL<Black,SmoothStep<Int<32768>,Int<0>>>,TrDelay<500>>,EFFECT_BOOT>,TransitionEffectL<TrConcat<TrConcat<TrFade<100>,AlphaL<Black,Int<16000>>,TrDelay<500>>,AlphaL<Black,Int<16000>>,TrFade<300>>,EFFECT_CLASH>>>(),
	StylePtr<OnSpark<Lockup<SimpleClash<BlastFadeout<ColorCycle<Pulsing<Black,SteelBlue,8000>,0,1,HumpFlicker<Sparkle<Rgb16<1662,7465,11366>,Rgb16<18641,20393,20996>>,Rgb16<26168,27558,30086>,50>,85,5000,500>,White>,White,50>,HumpFlicker<White,Rgb16<591,3350,5401>,50>,HumpFlicker<NavajoWhite,DarkOrange,50>>,White,300>>(),
	StylePtr<InOutTr<RandomFlicker<White,SteelBlue>,TrInstant,TrFade<500>,TransitionLoop<Black,TrConcat<TrConcat<TrDelay<5000>,Black,TrFade<2000>>,White,TrFade<2000>>>>>(),
	StylePtr<InOutTr<RandomFlicker<White,SteelBlue>,TrInstant,TrFade<500>,TransitionLoop<Black,TrConcat<TrConcat<TrDelay<5000>,Black,TrFade<2000>>,White,TrFade<2000>>>>>(), "Flynn"},
}

...

BladeConfig blades[] = {
  { 0, WS281XBladePtr<66, bladePin, Color8::GRBw, PowerPINS<bladePowerPin2, bladePowerPin3> >(),
       WS281XBladePtr<97, blade2Pin, Color8::GRB, PowerPINS<bladePowerPin1> >(),
       WS281XBladePtr<8, blade3Pin, Color8::GRB, PowerPINS<bladePowerPin4> >(),
       WS281XBladePtr<4, blade4Pin, Color8::GRB, PowerPINS<bladePowerPin5> >()
    , CONFIGARRAY(presets) },
};
