# Data Storage and Types in Java 

## A Unifying Mental Map: 

| Storage family              | Key idea                      | Typical concrete types          | Order preserved?           | Allows duplicates? | Key → Value? | Growth                         |
| --------------------------- | ----------------------------- | ------------------------------- | -------------------------- | ------------------ | ------------ | ------------------------------ |
| **Array**                   | Fixed‑length contiguous block | `int[]`, `String[]`             | Yes (index)                | Yes                | –            | Immutable length               |
| **Multi‑dimensional array** | “Array of arrays” recursion   | `int[][]`, `double[][][]`       | Per dimension              | Yes                | –            | Immutable length per sub‑array |
| **List**                    | Resizable ordered sequence    | `ArrayList<E>`, `LinkedList<E>` | Yes                        | Yes                | –            | Auto‑grows                     |
| **Set**                     | Mathematical set              | `HashSet<E>`, `TreeSet<E>`      | Hash → none, Tree → sorted | **No**             | –            | Auto‑grows                     |
| **Map**                     | Key–value lookup table        | `HashMap<K,V>`, `TreeMap<K,V>`  | Keys: hash/sorted          | Keys unique        | **Yes**      | Auto‑grows                     |

> All collections live in `java.util` and use generics: `List<Book>`, `Map<String, Integer>`

## Arrays - Zero overhead primitive type

* Object status: An array is an object, yet exposes only the read-only field length, with no other methods.
* creation and defaults:

```java
int[] a = new int[4];      // {0,0,0,0}
String[] s = new String[3]; // {null,null,null}
int[] b = {1,2,3};         // literal
```
Numeric cells default to 0, booleans to `false`, references to `null`. 
* **Time Costs**: O(1) indexed at a[i]; length immutability means resizing is automaitcally allocated and copied. 
  
## Multi-Dimensional Arrays - Arrays of Arrays

```java
double[][] rain = new double[13][32]; // months × days
```
Actually `rain` is an array whos elements are 13 seperate double[] objects; rows may be resized independently, enable jagged arrays. 

Indexing chains: `rain[m].length`, `rain[m][d]`
Nested loops traverse: `for(int m...) for (int d...)`

## Lists - Ordered Resizable sequences 

### 3.1 Core API (interface `List<E>`)

`add(e)`, `add(i,e)`, `get(i)`, `set(i,e)`, `remove(i|obj)`, `contains`, `size`, `isEmpty`, `clear`. 

For add(e) it appends the element to the end ofthe list.
for add(int index, e) the element is inserted at the position index. 
For get(i) it returns the value at that specified index
For set it sets the value at index i to element e. 
For remove it removes the firs toccurence of O using .equals. 
Clear removes all elements. 
size returns the array size of the list
isEmpty returns true or false. 

### 3.2 ArrayList<E> - Backed by a growable array
- Amortised through add(e), and get and stuff.
- Capacity doubles when exceeded; `ensureCapacity` hints.
- Permits `null`; unsynchronized. 
  
### 3.3 LinkList<E> - Double linked nodes:
- Implements both list and deque. Do not worry about this shit.

## Sets - Uniqueness enforcement
| Type               | Backing            | Order guarantee                      | Key costs                    |
| ------------------ | ------------------ | ------------------------------------ | ---------------------------- |
| `HashSet<E>`       | hash table         | **None** ([Oracle Documentation][1]) | O(1) add/contains (expected) |
| `LinkedHashSet<E>` | hash + linked list | Insertion order                      | Slightly more memory         |
| `TreeSet<E>`       | Red‑Black tree     | **Natural / Comparator order**       | O(log n) ops                 |

All permit a single null element. 

### Table:
| Purpose          | HashSet method                                      | TreeSet extra (sorted)                                            | Return / Behavior                   |
| ---------------- | --------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------- |
| **Create**       | `new HashSet<>()`                                   | `new TreeSet<>()`  `new TreeSet<>(Comparator)`                    | empty set                           |
| **Add**          | `add(e)`                                            | same                                                              | **true** if element was not present |
| **Remove**       | `remove(e)`                                         | same                                                              | **true** if element existed         |
| **Membership**   | `contains(e)`                                       | `ceiling(e)`, `floor(e)`, `first()`, `last()` for ordered queries | **boolean** or element              |
| **Bulk ops**     | `addAll(c)` `retainAll(c)` `removeAll(c)` `clear()` | range views: `subSet(from,to)`, `headSet(to)`, `tailSet(from)`    | —                                   |
| **Size / empty** | `size()` `isEmpty()`                                | same                                                              | **int / boolean**                   |
| **Iteration**    | `for (E e : set) { ... }`                           | iteration comes out **sorted**                                    | —                                   |
| **Null rules**   | One `null` element allowed                          | **null not allowed** (will throw `NullPointerException`)          |                                     |
| **Order**        | *Unordered* (hash bucket order)                     | **Natural / Comparator order**                                    |                                     |
| **Duplicates?**  | Always rejected – `add` returns `false`             |                                                                   |                                     |



## Maps - ASsociative lookups 
| Type                 | Order                                     | Nulls                          | Complexity   |
| -------------------- | ----------------------------------------- | ------------------------------ | ------------ |
| `HashMap<K,V>`       | none                                      | one null key, many null values | O(1) Average |
| `LinkedHashMap<K,V>` | insertion or access order                 | same as HashMap                | O(1)         |
| `TreeMap<K,V>`       | sorted by key (`Comparable`/`Comparator`) | **no null key**                | O(log n)     |

### Table:

| Purpose               | Method / Field                                                                                | Result or Behavior (return value bolded)                      |
| --------------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| **Create**            | `new HashMap<>()`  `new HashMap<>(cap, load)`                                                 | empty map                                                     |
| **Insert / update**   | `put(k,v)`                                                                                    | **previous V** or `null` if none                              |
|                       | `putIfAbsent(k,v)`                                                                            | **current V** or `null` (value left unchanged if key present) |
|                       | `merge(k,v,f)`                                                                                | combines old/new via function `f`                             |
| **Retrieve**          | `get(k)`                                                                                      | **V** or `null`                                               |
|                       | `getOrDefault(k,def)`                                                                         | **V** or **`def`**                                            |
| **Presence test**     | `containsKey(k)` `containsValue(v)`                                                           | **boolean**                                                   |
| **Remove**            | `remove(k)`                                                                                   | **old V** or `null`                                           |
|                       | `remove(k,v)`                                                                                 | **true** if pair removed                                      |
|                       | `replace(k,v)` `replace(k,old,new)`                                                           | previous V / **boolean**                                      |
| **Bulk ops**          | `putAll(map)` `clear()`                                                                       | —                                                             |
| **Size / empty**      | `size()` `isEmpty()`                                                                          | **int / boolean**                                             |
| **Views for looping** | `keySet()` → `Set<K>`<br>`values()` → `Collection<V>`<br>`entrySet()` → `Set<Map.Entry<K,V>>` | live, backed views                                            |
| **Iteration idiom**   | `for (Map.Entry<K,V> e : map.entrySet()) { ... }`                                             | fastest (allows `e.getKey() / getValue()`)                    |
| **Null rules**        | One `null` key allowed; values may be `null`                                                  |                                                               |
| **Order**             | *None* (use `LinkedHashMap` or `TreeMap` for order)                                           |                                                               |

Essentials:
```java
Map<String,Integer> freq = new HashMap<>();
freq.put("apple", 3);
freq.merge("apple", 1, Integer::sum);   // handy adder
int n = freq.getOrDefault("pear", 0);

for (Map.Entry<String,Integer> e : freq.entrySet()) {
    System.out.printf("%s → %d%n", e.getKey(), e.getValue());
}
```



