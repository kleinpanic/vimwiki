// "strudel 1.1 demo"

$: note("<d d d a a# d3 f4>*15".sub(12))
  .gain(1).s("sawtooth").fanchor(0)
  .lpf(mousex.range(0,1000)).lpenv(mousey.range(0,8))
  .ftype('ladder')
  .room(2.5)
  .lpq(7).color('cyan')
  // .drive(3)
  .distort("1.5:.7")
  ._scope()

$: s("bd*5").bank('RolandTR909')
._punchcard({height:16,labels:1})
$_: s("hh*10").dec(.1).bank('RolandTR909').gain(sine.fast(4).room(2.5))
._punchcard({height:16,labels:1})
$: gain("[0 1]*2.5").chord("<Dm9 Gm9>").voicing()
  .delay(".6:.1:.8").room(1).dec(.1).s("sine").fm(2)
  .lastOf(4, x=>x
    .gain("[.3 1]*5")
    .add(note(saw.mul(2)))
    .struct("x*20")
    .dec(.1).delay(0))
    .room(2.5)
._pitchwheel()

$: gain("[0 1]*2.5").chord("<Dm9 Gm9>").voicing()
  .delay(".6:.1:.8").room(5).dec(.2).s("sine").fm(5)
  .lastOf(4, x=>x
    .gain("[.3 1]*7")
    .add(note(saw.mul(2)))
    .struct("x*20")
    .dec(.7).delay(5))
    .room(2.5)
._pitchwheel()

all(x=>x.color('cyan'))


