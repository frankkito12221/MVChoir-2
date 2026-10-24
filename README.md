# MV CHOIR//LAB  v2.1  (Manana Vemos)

Dos plugins VST3 que comparten el mismo motor de voces naturales (cambio de tono conservando los formantes):

1. **MV CHOIR LAB** (EFECTO): se carga en un inserto del mezclador con una voz real. Arma el coro con 10 voces
   (MAIN, HARMONY 1-4, DOUBLER 1-2, TEXTURE, GHOST, FX LAYER) y exporta stems.
2. **MV CHOIR LAB KEYS** (INSTRUMENTO): cargas una grabacion tuya de "aaah" y la tocas con el teclado MIDI.
   Una tecla = un acorde (estilo Omnichord) o cada tecla = una nota. Salidas separadas: bajo, tenor, alto, soprano.

## Obtener los plugins (gratis, sin instalar nada)
1. Repositorio de GitHub: subi TODO el contenido de este ZIP (carpetas `Source`, `Assets`, `tools`, `.github` y
   los archivos sueltos). Si `.github` no sube: "Add file > Create new file", nombre `.github/workflows/build.yml`.
2. Pestana **Actions**: compila solo (15-20 min). Con el check verde baja `MV-CHOIR-LAB-Windows`.
   Adentro hay DOS archivos sueltos: `MV CHOIR LAB.vst3` y `MV CHOIR LAB KEYS.vst3`.
   (Si el de KEYS no aparece, el efecto igual se compilo: avisame y mandame el error de esa pestana.)
3. Copia los archivos a `C:\Program Files\Common Files\VST3` (o a tu carpeta de plugins) y en FL:
   Options > Manage plugins > Find installed plugins.

## KEYS: como se usa
- Carga una grabacion (boton LOAD VOICE o arrastrala): una vocal sostenida, una sola voz, seca, sin reverb.
  El plugin detecta el tono solo (ROOT NOTE / ROOT FINE); si lo detecta mal, ajustalo a mano.
- MODE: CHORD = la tecla es la raiz de un acorde (12 tipos). DIRECT = cada tecla es una nota.
- STRUM, UNISON (copias por nota), ATTACK/RELEASE, DETUNE/HUMANIZE/MOVEMENT/WIDTH, BRIGHT/FORMANT, MUTATION, reverb.
- Salidas: en FL, boton del plugin > Processing/outputs: activa Bass, Tenor, Alto, Soprano y rutealas al mezclador.
- REC STEMS: graba BASS, TENOR, ALTO, SOPRANO y MIX en `Documentos\MV CHOIR LAB\Stems`.
- Latencia ~46 ms (el motor necesita mirar un poco hacia adelante). FL la compensa al reproducir; al tocar en vivo
  se nota un pequeno retraso.

## Pruebas del motor (sin JUCE)
`g++ -O2 -std=c++17 tools/test_engine.cpp -o test_engine && ./test_engine`
`g++ -O2 -std=c++17 tools/test_keys.cpp -o test_keys && ./test_keys`
