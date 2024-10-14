# Vi and Vim
## Vi 
- A screen-oriented text editor orignally created for the Unix System. The portable subset of the behavior of vi and programs based on it and the ex editor language supported wit hthese prgrams, is described by the Single Unix Specifications and POSIX.
- Originally the code for vi was written by Bill Joy in 1976, as the visual mode for a line editor called ex that Joy had written with Chuck Haley. Bill Joy's ex 1.1 was released in March 1978. It was not until version 2.0 of ex, released as part of Second BSD in May 1979, that the editor was installed under the name vi (Which took users directly into ex's visual mode), ad the name by which it is known today. Some current implementations of vi can trace their source code ancestry to Bill Joy; and others are completely new. 
- The name "vi" is derived from the shortest unambiguous abbreviation of the ex command visual, which switches the ex line editor to its full-screen mode 
  
### Creation
- vi was derived from a sequence of UNIQ command line editors, starting with ed, which was a line editor designed to work well on teleprinters, rather than display terminal. 
- Ed was enhanced in 1976, making em, which was designed for display termins and was a single-line-at-a-time visual editor. 
- Bill Joy and Chuck Baley, took code from em and ed to make en, and then "extended" en to create ex version 0.1.
- Vi and ex shaire their code; vi is the ex binary launching with the capabilitiy to render the text being edited onto a computer terminal-it is ex's visual mode. The name vi comes from the abbreviated ex command vi to enter visual mode from within it. 
### Interface
- Vi is a modal editor: It operates in either insert mode (where typed text becomes part of the document) or command mode (Where keystrokes are interpreted as commands that control the edit session). 

### Complete VI Key Binding List
a - Enter insertion mode after current character
b - back word
c - change command
d - delete command
e - end of word
f - find character after cursor in current line
g - UNBOUND
h - Move left one character
i - Enter insertion mode before current character
j - move down one line
k - move up one line
l - move right one character
m - mark current line and position
n - repeat last search
o - pen line below and enter isertion mode
p - put buffer after cursor
q - UNBOUND
r - replace single character at cursor
s 
t 
u 
v 
w 
x 
y
z
A 
B 
C 
D 
E 
F 
G
H 
I 
J 
K 
L 
M 
N 
O 
P 
Q
R 
S 
T 
U 
V 
W 
X 
Y 
Q 
0 
1-9 
! 
@
# 
$
%
^
&
*
(
)
|
-
_
=
+
[
]
{
}
;
'
`` 
:
"
~
,
.
/ 
<
?
^A 
^B 
^C 
^D 
^E 
^F 
^G 
^H 
^I 
^J 
^K 
^L 
^M 
^N 
^O 
^P 
^Q 
^R 
^S 
^T 
^U 
^V 
^W 
^X 
^Y
^Z
^[
^\
^]
^^
^_
^?
