<!-- .slide: class="time-slicing bulletpoints" -->
## (virtualisierter) RAM
* Phys. Speicher / RAM addressiert via **`0x0000.. - 0xFFFF..`**
* unterteilt in **Pages** (Blöcke fester Größe)
* Auslagern von Pages auf Festplatte möglich (**langsam!**)
    * **Swap** / swapping auf Linux/Unix/macOS
    * **Pagefile** in Windows
* *Hugepages*?
* Virtueller Speicher **gemappt** auf physikalischen Speicher

notes: 
* Apps gehen von alleiniger Nutzung des RAM aus


---


<!-- .slide: class="time-slicing" -->
## (virtualisierter) RAM
*Page Size* (in Bytes) auf echten Systemen

```bash
$ getconf PAGE_SIZE
4096
```

*Hugepages* aktiviert/verfügbar?
```bash
$ mount | grep huge
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
```


---


## (virtualisierter) RAM

### <!-- .element: class="fragment" data-fragment-index="7" --> <br/>Physikalisch: `[0x00]` <span style="color: green;">`[0x01]`</span> <span style="color: red;">`[0x02]`</span> `[0x03]`<span style="color: green;">`[0x04]`</span> <span style="color: red;">`[0x05]`</span>
---
### <!-- .element: class="fragment" data-fragment-index="2" --> <i class="fab fa-adobe" style="color: red;"></i> <span style="color: red;">`[0x00]` `[0x01]`</span> `[0x02]` `[0x03]` `[0x04]` `[0x05]`
### <!-- .element: class="fragment" data-fragment-index="3" --> <i class="fab fa-android" style="color: green;"></i> <span style="color: green;">`[0x00]`</span> `[0x01]` `[0x02]` <span style="color: green;">`[0x03]`</span> `[0x04]` `[0x05]`
---
### <!-- .element: class="fragment" data-fragment-index="4" --> *Page Table*:
### <!-- .element: class="fragment" data-fragment-index="5" --> <i class="fab fa-adobe" style="color: red;"></i> <span style="color: red;">`[0x00]`</span> `  -->  [0x02]`<br/> <i class="fab fa-adobe" style="color: red;"></i> <span style="color: red;">`[0x01]`</span> `  -->  [0x05]`
### <!-- .element: class="fragment" data-fragment-index="6" --> <i class="fab fa-android" style="color: green;"></i> <span style="color: green;">`[0x00]`</span> `  -->  [0x01]`<br/><i class="fab fa-android" style="color: green;"></i> <span style="color: green;">`[0x03]`</span> `  -->  [0x04]`
---
### <!-- .element: class="fragment" data-fragment-index="1" --> Physikalisch: `[0x00] [0x01] [0x02] [0x03] [0x04] [0x05]`

notes: 
* Apps gehen von alleiniger Nutzung des RAM aus


---


<!-- .slide: class="time-slicing" -->
## (virtualisierter) RAM
Verfügbarer Speicher/Swap

```bash
$  free -m
              total        used        free      shared  buff/cache   available
Mem:          15951        2143         240           3       13567       13473
Swap:          2047         138        1909
```