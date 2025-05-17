# Methods and Fields Need to Knows

Below is a **single, tall table** (3 columns) covering every method / field specifically named in the course units and reviews you provided.  Read straight down to refresh what each call is for and which type exposes it.

| Method / Field                                             | Belongs to → Type(s) that define it         | Purpose & Return‑value (what it “does”)                                                   |
| ---------------------------------------------------------- | ------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **length** (field)                                         | array objects (`int[]`, `String[]`, …)      | Read‑only size of the array (first legal index = 0, last = `length‑1`).                   |
| **length()**                                               | `String`                                    | Returns number of UTF‑16 code units in the string.                                        |
| **equals(other)**                                          | `String`, all objects                       | `boolean` – true when contents (or semantics) match.                                      |
| **charAt(index)**                                          | `String`                                    | `char` at given position (0‑based).                                                       |
| **startsWith(str)**                                        | `String`                                    | `boolean` – true if receiver begins with `str`.                                           |
| **endsWith(str)**                                          | `String`                                    | `boolean` – true if receiver ends with `str`.                                             |
| **substring(begin,end)**<br>**substring(begin)**           | `String`                                    | New substring from *begin* (inclusive) to *end* (exclusive) / to end of string.           |
| **indexOf(str)**                                           | `String`                                    | First index of `str` or `‑1` if absent.                                                   |
| **toLowerCase()**                                          | `String`                                    | New string with locale‑aware lower‑casing.                                                |
| **toUpperCase()**                                          | `String`                                    | New string with locale‑aware upper‑casing.                                                |
| **add(e)**                                                 | `List<E>`, `ArrayList<E>`, `HashSet<E>`     | List → appends element; returns `true`.<br>Set → inserts if not present; `true` if added. |
| **add(index,e)**                                           | `List<E>`                                   | Inserts at index, shifting later items.                                                   |
| **get(index)**                                             | `List<E>`                                   | Returns element at position.                                                              |
| **set(index,e)**                                           | `List<E>`                                   | Replaces and returns old element.                                                         |
| **remove(index)**                                          | `List<E>`                                   | Removes & returns element at index.                                                       |
| **remove(obj)**                                            | `List<E>`, `Set<E>`                         | Deletes first equal element; `boolean` success.                                           |
| **contains(obj)**                                          | `List<E>`, `Set<E>`                         | `boolean` – membership test.                                                              |
| **size()**                                                 | all `Collection` types, arrays via `length` | Current element count.                                                                    |
| **isEmpty()**                                              | all `Collection` types                      | `true` when size 0.                                                                       |
| **clear()**                                                | all `Collection` types                      | Removes every element.                                                                    |
| **iterator()**                                             | all `Collection` types                      | Returns `Iterator<E>` for explicit looping.                                               |
| **put(k,v)**                                               | `HashMap<K,V>`                              | Associates value; returns previous V or `null`.                                           |
| **putIfAbsent(k,v)**                                       | `HashMap<K,V>`                              | Adds only if key missing; returns existing or `null`.                                     |
| **merge(k,v,fn)**                                          | `HashMap<K,V>`                              | Combines old/new via `BiFunction`; returns final V.                                       |
| **get(k)**                                                 | `HashMap<K,V>`                              | Returns value or `null` if key absent.                                                    |
| **getOrDefault(k,def)**                                    | `HashMap<K,V>`                              | Value or supplied default.                                                                |
| **containsKey(k)**                                         | `HashMap<K,V>`                              | `boolean` key presence.                                                                   |
| **containsValue(v)**                                       | `HashMap<K,V>`                              | `boolean` value presence (linear scan).                                                   |
| **remove(k)**                                              | `HashMap<K,V>`                              | Deletes entry; returns old V or `null`.                                                   |
| **remove(k,v)**                                            | `HashMap<K,V>`                              | `boolean` – removes only if mapping matches.                                              |
| **replace(k,v)**<br>**replace(k,old,new)**                 | `HashMap<K,V>`                              | Overwrites value; returns previous V / `boolean` success.                                 |
| **keySet()**                                               | `HashMap<K,V>`                              | Live `Set<K>` view of keys.                                                               |
| **values()**                                               | `HashMap<K,V>`                              | Live `Collection<V>` view of values.                                                      |
| **entrySet()**                                             | `HashMap<K,V>`                              | `Set<Map.Entry<K,V>>` view for key‑value pairs.                                           |
| **putAll(map)**                                            | `HashMap<K,V>`                              | Bulk copy of another map’s entries.                                                       |
| **Map.Entry.getKey()**                                     | `Map.Entry<K,V>`                            | Returns key from an entry view.                                                           |
| **Map.Entry.getValue()**                                   | `Map.Entry<K,V>`                            | Returns value from an entry view.                                                         |
| **addAll(coll)**                                           | `HashSet<E>`, `TreeSet<E>`                  | Inserts every element from collection; returns `true` if set changed.                     |
| **retainAll(coll)**                                        | `HashSet<E>`, `TreeSet<E>`                  | Keeps only elements also in `coll`; boolean changed.                                      |
| **first()**, **last()**                                    | `TreeSet<E>`                                | Smallest / largest element (sorted order).                                                |
| **ceiling(e)**, **floor(e)**                               | `TreeSet<E>`                                | Least ≥ e / greatest ≤ e; `null` if none.                                                 |
| **headSet(to)**, **tailSet(from)**,<br>**subSet(from,to)** | `TreeSet<E>`                                | Range‑view sets (live, backed).                                                           |
| **toString(array)**                                        | `java.util.Arrays` (static)                 | Pretty string `"[a, b, c]"`.                                                              |
| **copyOf(array,newLen)**                                   | `Arrays`                                    | Duplicates array to given length.                                                         |
| **sort(array)**                                            | `Arrays`                                    | In‑place ascending sort (dual‑pivot quicksort for primitives).                            |
| **fill(array,val)**                                        | `Arrays`                                    | Assigns `val` to every cell.                                                              |
| **equals(a,b)**                                            | `Arrays`                                    | Content equality (`boolean`).                                                             |
| **compare(a,b)**                                           | `Arrays`                                    | Lexicographic comparison (`int` <0, 0, >0).                                               |
| **next()**                                                 | `Scanner`                                   | Reads next whitespace‑delimited token (as `String`).                                      |
| **nextLine()**                                             | `Scanner`                                   | Consumes rest of current line (including empty).                                          |
| **nextInt()**                                              | `Scanner`                                   | Parses next token as `int`.                                                               |
| **println(x)**                                             | `PrintWriter`, `System.out`                 | Prints `x` plus newline.                                                                  |
| **print(x)**                                               | `PrintWriter`, `System.out`                 | Prints without newline.                                                                   |
| **printf(fmt,args)**                                       | `PrintWriter`, `System.out`                 | Formatted print; returns the writer for chaining.                                         |

> **Remember:**
>
> * Arrays expose **only** the `length` field; all other conveniences live in `java.util.Arrays`.
> * `HashSet` shares all `Collection` methods, but `add`, `contains`, `remove` are the ones you actually call day‑to‑day.
> * `TreeSet` adds order‑aware navigation (`first`, `ceiling`, range views) on top of the basic `Set` API.
> * Loop idioms rely on these APIs: `for(E e : list)`, `for(Map.Entry<K,V> e : map.entrySet())`, nested `for` for multi‑dim arrays.

