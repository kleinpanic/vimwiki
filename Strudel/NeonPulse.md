/*───────────────────────────────────────────────────────────────
  STRUDEL 𝟏.𝟏 – COMPLEX EDM ARRANGEMENT
───────────────────────────────────────────────────────────────*/

/*--- 1.  KICK + SNARE GRID  -----------------------------------*/
$:
s("<bd bd ~ bd>*8 [sn ~]*4")          // asymmetric four‑on‑the‑floor
 .bank('RolandTR909')
 .gain(1)
 .dec(.15)
 .room(0.5)
 /* subtle eight‑bar “fill” – more punch & drive */
 .lastOf(8, x => x
   .gain(1.3)
   .distort("1.5:.7")
   .struct("x*32")                    // rapid flam‑fill
   .room(2)
 )
 ._punchcard({height:16, labels:1})


/*--- 2.  HI‑HAT TEXTURE  --------------------------------------*/
$:
s("hh*8")                             // eight 16ths / cycle
 .bank('RolandTR909')
 .dec(.06)
 .gain(sine.fast(4))                  // tremolo shimmer
 /* every 4 cycles reverse the pattern, every 16 double density */
 //.every(4,  p => p.reverse())
 .every(16, p => p.struct("x*32"))
 ._punchcard({height:16})


/*--- 3.  BASSLINE – MORPHING FILTER ---------------------------*/
$:
note("<d2 g2 f2 a#1>*8".sub(0))       // modal riff (D‑G‑F‑A#)
 .s("sawtooth")
 .gain(.85)
 /* animated low‑pass sweep */
 .lpf(saw.range(200,1200))
 .lpenv(sine.fast(.5).range(0,6))
 .ftype('ladder')
 .lpq(6)
 .distort("1.3:.6")
 /* octave jump + boost every 8 cycles */
 .lastOf(8, x => x
   .add(note(12))                     // +12 st = octave
   .gain(1.15)
 )
 .color('cyan')
 ._scope()                            // visualise contour


/*--- 4.  CHORD STABS / PAD SWELLS -----------------------------*/
$:
gain("[.6 .8 1 .8]*2")                // micro‑dynamics
 .chord("<Dm9 Gm9 A#maj7 C6>")        // 4‑bar progression
 .voicing()                           // spread notes pleasantly
 .s("sine")                           // pure, glassy pad
 .fm(2)
 .delay(".5:.2:.7")
 .room(.9)
 .dec(.25)
 /* stab bursts on last beat of every 4th bar */
 .lastOf(4, x => x
   .struct("x*16")
   .gain("[.3 1]*5")
 )
 ._pitchwheel()                       // vertical modulation wheel

$:
gain("[.7 .9 2 .9]*2")                // micro‑dynamics
 .chord("<Dm9 Gm9 A#maj7 C6>")        // 4‑bar progression
 .voicing()                           // spread notes pleasantly
 .s("square")                           // pure, glassy pad
 .fm(3)
 .delay(".5:.2:.7")
 .room(1.0)
 .dec(.25)
 /* stab bursts on last beat of every 4th bar */
 .lastOf(4, x => x
   .struct("x*16")
   .gain("[.3 1]*5")
 )
 ._pitchwheel()

/*--- 5.  ARPEGGIATED LEAD  ------------------------------------*/
$:
note("arp <d4 f4 a4 c5>*16")          // cascading 16‑note arp
 .s("triangle")
 .gain(.7)
 .fm(3)
 .delay(".25:.05:.5")
 .lpf(saw.range(500,2000))
 .lpenv(sine.fast(2).range(0,8))
 .lpq(4)
 .distort("1.1:.5")
 /* flip direction every 8, deep fade‑in octave drop every 16 */
 //.every(8,  p => p.reverse())
 .lastOf(16, p => p
   .sub(12)                           // drop an octave briefly
   .gain(.9)
 )
 .color('cyan')

$:
note("arp <d4 f4 a4 c5>*16")          // cascading 16‑note arp
 .s("sawtooth")
 .gain(2.0)
 .fm(5)
 .delay(".35:.15:.15")
 .lpf(saw.range(500,1000))
 .lpenv(sine.fast(2).range(0,8))
 .lpq(4)
 .distort("1.1:.5")
 /* flip direction every 8, deep fade‑in octave drop every 16 */
 //.every(8,  p => p.reverse())
 .lastOf(16, p => p
   .sub(12)                           // drop an octave briefly
   .gain(.9)
 )
 .color('cyan')


/*--- GLOBAL COLOUR TREATMENT ----------------------------------*/
all(x => x.color('cyan'))

/*───────────────────────────────────────────────────────────────
  PERFORMANCE NOTES
───────────────────────────────────────────────────────────────
  • The piece is designed to run continuously; the internal
    pattern transforms (reverse, struct, lastOf, etc.) ensure
    that no 8‑bar span is identical to any other.
  • Filter sweeps, FM depth, distortion, and gain all ride on
    slow LFOs (sine / saw) so timbres breathe over time.
  • To create breakdowns / drops on the fly, simply mute or
    re‑evaluate individual $: blocks, tweak .gain(), or change
    .delay()/room parameters.
  • Visual helpers (_scope, _punchcard, _pitchwheel) can be
    closed when you’re ready to perform.
───────────────────────────────────────────────────────────────*/

