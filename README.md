# Virtual Guitar Rig Simulator

Uno studio virtuale per chitarra elettrica che gira interamente nel browser: scegli una chitarra, costruisci la tua catena di pedali, ampli e casse, e ascolta il risultato in tempo reale. Nessun backend, nessuna installazione, nessuna dipendenza: è **un unico file HTML** (`index.html`) con HTML, CSS, JavaScript e DSP basato su Web Audio API.

> Tutti i controlli sono collegati al motore audio: non è un mockup grafico.

**Demo online: https://vincenzoboellis.github.io/virtualguitarrig/**

## Utilizzo

- **In locale:** apri `index.html` in Chrome, Edge, Firefox o Safari recenti, oppure avvia un piccolo server, ad esempio `python3 -m http.server` e vai su `http://localhost:8000`.

Premi **Play** per sentire la chitarra interna, oppure scegli "Ingresso audio" per collegare la tua chitarra (usa le cuffie per evitare feedback) o "File audio" per importare un WAV/MP3.

## Funzionalità

**Chitarre**
- 7 modelli: Stratocaster, Telecaster, Les Paul, SG, PRS, Superstrat e pickup attivi (stile).
- Configurazioni SSS, HSS, HSH, HH, SS; 12 tipi di pickup, coil split, selettore, volume, tono, legno, corde, accordatura, plettro.
- Chitarra interna sintetizzata a guida d'onda (Karplus-Strong) con modello di pickup, 10 pattern dimostrativi e accordi cliccabili.
- Chitarra reale tramite l'ingresso audio, con profili timbrici (solo equalizzazione), e importazione di file WAV/MP3.

**Pedali (34)**
- Dynamic e Gain: clean boost, overdrive, distortion, fuzz, compressor, limiter, noise gate, noise suppressor.
- Modulation: chorus, flanger, phaser, tremolo, vibrato, rotary, uni-vibe.
- Time based: delay analogico, digitale, a nastro, slapback, ping pong; reverb, spring, plate, hall, room.
- Filter e pitch: wah, auto wah, envelope filter, EQ grafico e parametrico, octaver, pitch shifter, harmonizer, ring modulator.
- Tutti hanno dimensione uguale, parametri principali in evidenza e gli altri nel pannello di controllo.

**Amplificatori e casse**
- 11 modelli: 6 valvolari (Vintage Clean, American Clean, British Crunch, British High Gain, Modern High Gain, Boutique) e 5 a transistor (Solid State Clean, Crunch, Modern High Gain, Jazz Clean, Metal).
- Disponibili come testata, combo, preamp o finale di potenza, con canali, tone stack, presence, resonance, master e sag.
- Casse 1x8, 1x10, 1x12, 2x12, 4x10, 4x12 con 8 altoparlanti, 4 microfoni (dinamico, dinamico grande, condenser, ribbon), posizione, distanza, due microfoni mixabili e **caricamento di IR WAV personalizzate**.

**Catena del segnale**
- Pedalboard con drag and drop (mouse e touch), riordino dalla barra della catena, duplica, bypass, solo, routing parallelo.
- Due processori multieffetto con blocchi riordinabili e patch salvabili.
- 17 preset di fabbrica (Clean, Funk, Blues, Classic Rock, Hard Rock, Heavy Metal, Thrash, Modern Metal, Djent, Shoegaze, Ambient, Post Rock, Indie, Alternative, Lead, Vintage Rock, Solo High Gain).
- Salvataggio nel browser, esportazione e importazione JSON, confronto A/B tra due configurazioni e tra segnale originale ed elaborato.

**Strumenti**
- Metronomo, tap tempo, accordatore cromatico, noise gate globale, EQ finale, limiter, meter con clipping, spettro e forma d'onda.
- Registrazione in tempo reale ed esportazione WAV, oppure render offline più veloce del tempo reale.

## Compatibilità

| Funzione | Requisito |
|---|---|
| Audio e effetti | Web Audio API (tutti i browser moderni) |
| Latenza minima | AudioWorklet (Chrome, Edge, Firefox e Safari recenti, da HTTPS o localhost) |
| Chitarra reale | `getUserMedia`, richiede HTTPS o localhost |
| Selezione dell'uscita audio | `AudioContext.setSinkId` (solo alcuni browser) |

Se il browser non riesce a caricare l'AudioWorklet (ad esempio aprendo il file direttamente da disco in alcuni browser) l'app passa automaticamente a una **modalità compatibile** basata su `ScriptProcessorNode`: stesso suono, latenza leggermente maggiore.

## Come è fatto

- Un solo file, senza build e senza librerie esterne.
- Motore modulare: ogni dispositivo è un nodo indipendente che può essere collegato, scollegato, riordinato e bypassato.
- DSP: waveshaping con oversampling, saturazione valvolare e a transistor, sag, filtri, delay con feedback, modulazione, riverberi e casse per convoluzione con risposte all'impulso sintetiche a fase minima, pitch shifting granulare, rilevamento dell'intonazione (YIN).
- Gain staging calibrato: gli ampli e i preset sono livellati per avere volumi simili.

## Limiti noti

- Tutti i modelli sono **approssimazioni DSP** ispirate a categorie di apparecchi: non sono repliche fedeli di hardware analogico.
- I profili timbrici per la chitarra reale sono solo equalizzazioni.
- L'harmonizer in modo Scala funziona su una nota alla volta ed è sperimentale; octaver e pitch shifter sono granulari e hanno qualche decina di millisecondi di latenza.
- Le immagini delle chitarre e dei pedali sono illustrazioni in SVG/CSS, non foto.
- La latenza reale dipende da browser, sistema operativo e scheda audio.

## Marchi

Nomi come Stratocaster, Telecaster, Les Paul, SG, PRS e simili sono marchi dei rispettivi proprietari e sono usati solo in forma descrittiva ("stile"). Questo progetto non è affiliato né approvato da alcun produttore.

## Licenza

Rilasciato con licenza [MIT](LICENSE).

---

## English summary

A browser-based virtual guitar rig: guitar models, 34 pedals, 11 tube and solid-state amp models, cabinets with virtual mics and custom IR loading, drag and drop pedalboard, parallel routing, multi-FX, 17 presets, tuner, metronome, recording and WAV export. Single HTML file, no backend, no dependencies, built on the Web Audio API and AudioWorklet (with an automatic ScriptProcessor fallback). All models are DSP approximations, not exact replicas of real hardware. Licensed under MIT.
