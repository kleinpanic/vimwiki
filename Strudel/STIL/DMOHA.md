// "(4S,4aS,8aR)-4,8a-Dimethyloctahydronaphthalen-4a(2H)-ol dub" @by superlocrianlizardbuzzard

// minimal synth colors
// writing a string comprising several lines with backticks ``
$: note(`<
[<[[d4] [g3]] [d4, d5]>] [- [[a#3, a#4] [a3, a4]@7] [e4, e5]] [<[a4, a5] -> <- - [d4, d5]> [g3, g4]] [[a#3, a#4] [f4, f5]] [-] [-]
<[e3, e4] [e4 d4]> <[d3, d4] [d4 db4]> [g3,g4] [f#3@5, f#4@5 -] [e3, e4] <- - [- b3, b4]>
>/2`.sub(0))
.s("[square, sawtooth]").fm(3)
  .adsr("[.2:2:.2:.2]")
  .lpf(277).lpenv(5).lpa(-1).lpd(-1).lpq(3)
  .distort("[2:.1]")
  .velocity(perlin.range(0.5, 0.3).slow(1.5))
  .late(perlin.range(0.04, 0.3).slow(2))
  .gain(.7)
  .mask("<0!12 1!8 0!12 1!4 0!4>")
  .when("<0!8 1!4 0!12>", x=>x.hush())
  .when("<0!24 1!4>", x=>x.hush())
.room("[.3, .5]")
  //.hush()

setcps(150/60/4)

const drumstruct = "Linn9000"

// synth build on pentatonics and accidentals
// raising a note with an accidental behind the note
$: n(`<
  <[1,2,3,4,5,6]!2 [0, 1,7,3,9,5,6]>
  [ <[0,1, 2, 3, 4, 5, 8, 7, 6, 5]!2 [0,1 ,2 , 7, 6, 5, 3, 4, 5, 8]>] 
  <[0, 1#,2#,3,4,5,6]!6 [6#,2#,9#,5,11]>
  <[0bb, 2bb, 3bb, 4bb, 5bb, 6bb] [0##, 2#, 3##, 4#, 5##]>
  >`)
  .scale("<G!12 E!12>:<minor!2 major!2>:pentatonic")
  .s("triangle").adsr("[<.1 .125 .15 .2 .3 .4 .35 .25 .12>/3:1:0:0]")
.lpf(777).lpa(2.8).lpf(777).lpf(777).lpenv("<2>")
  .fm("<1.5 2.5 3.5 4.5 3.5 2.5>/3").fmh(".99").fmenv(-.2).vib("<6!5 5>:.2")
  .room(.5)
  .velocity(.1)
.hpf(999)
.mask("<0!7 1!999>")

// pianos build on pentatonics and accidentals
// regarding tonality change, G major is close to E minor, so G minor / major switching to E minor / major is subjectively smooth enough
$: n(`
  <
  < [0, 2, 5, 6]!2 [1,7,3,9,5,6]>
  [ [0,1, 2],      <[ 8, 7, 6]!2  [- 7 [6, 5] [3, 4] 5 8]!1>] 
  <[0, 1#,2#,3,4,5,6]!6 [6#,2#,9#,5,11]>
  <<[0bb, 2bb, 3bb 4bb 5bb 6bb]  [0bb, 2bb, 3bb, 4bb, 5bb, 6bb]> [0##, 2#, 3##, 4#, 5##]>
  >
  `).scale("<G2!12 E2!12>:<minor!2 major!2>:pentatonic")
  .s("kawai")
  .delay("[.3:.1:.3]")
  .room(.2).rlp(50)
.velocity("<.7 .5>*<1 8 1 4>".sub(.3))
.clip(1.7)
.hpf(555)
//.hush()

// kick drum 
$: note("<g1!3 e1!3>/4")
  .sound("sine")
  .penv(32).pdec(0.2)
  .adsr("0:1:0:0")
  .pcurve(1)
  .velocity(5)
  .lpf(33)
  .coarse("<0!4 4!4>/4")
  .mask("<1 0!3>")

// drums - when chaining functions, it does not matter if there is a whitespace in between
const sweep = 9

$: stack(
s("bd").struct("x(<3!4 5 3!3>, 8, <0 2 0 1 0 1>)")  .bank("RolandTR606") .gain("[2 1 1]") .mask("<0!8 1!992>")
  ,
s("hh").struct("x(<7 9 9 8 9 13>, 16, <0 0 2 0>)").velocity("<.5 .2>*<16!3 8!3 16!2>".add(0))   .bank(drumstruct)
    .speed(cosine.range(1.15, 1.35).slow(sweep)) .mask("<0!4 1!996>")

  .when("<0!8 1!8>", x=>x.superimpose(x=>x.gain(.1).late(1/16)))
  ,
  s("<rim>").struct("x(<0 [2 0]>, 4, 2)").room("<.1!3 .2 >/2") .speed("[.79, .8]")  .bank(drumstruct) .gain(.4) .fast("<1!4 2!8>")
  ,
  s("[cp, <->]").struct("x(<0 1>, 8, <2 4>)*<1!6 2!2>").room("<.3!3 .4 >/2") .speed("[1.11, 1.14]")  .bank("LinnDrum") .gain(.05)
  .fast("<1!6 2!2>").hpf(1111).mask("<0!8 1!8>")
  )
  .superimpose(x=>x.speed(cosine.range(1.15, 1.35).slow(sweep + 0.1).gain(.4))
)
  .lpf(2222).ftype("12db").late("<0 0.01>*2")

// bass
$: n("<<4!9 5 4!2> 3 <1!5 1b> 0 0 1 <2 2 2 1> 3>*<4!5 5>")
  .add(5)
  .scale("<G1!12 E1!12>:<minor major>:pentatonic")
  .s("gm_acoustic_bass:1")
.velocity("<1.8 1.1>*<4!5 5>".add(1.5))
  .lpf(222)
.ply("<1!8 1!4 2!2 1!2>")
.mask("<0!8 1!992>")
.when("<0!16 1!8>", x=>x.struct("[x@1 x@3]*<4!5 5>").velocity("<[2.3 1.1@3][1.8 1.1@3]>*<4!5 5>"))

// imposing a rhythmn on everything with all, when, an arrow function and struct
all(
  x=>x.hpf("<999 888 777 667 0!999>/2")
  .postgain(.5)
  .when("<0!8 1!4 0!12>", x=>x.struct("x(3,8)")
  .stack(s("[cp(<0 0 0 3>,8)]").speed("[1.11, 1.14]").bank(drumstruct))
  .lpf(saw.range(222, 2222).slow(4)).shape(saw.range(.1, .5).slow(4)))

  .when("<0!24 1!4>", x=>x.struct("x(5,8)").lpf(saw.range(222, 2222).slow(4)) .shape(saw.range(.1, .5).slow(4)).ply("<1!24 1!4 1!24 1 [1 2] [1 2] 2 1!999>"))
   )
    
    
  


