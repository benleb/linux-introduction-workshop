<!-- .slide: class="chapter" -->
# Scripts 📓✍️
<br/><br/>

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
# Scripts

#### Write commands in a file instead a Terminal

# 💁‍♀️

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
# Scripts
* one command per line - or separated by **`;`**
* write a **`shebang`** in the first line of that file
* start with **`./script.sh`**

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
# **`shebang`**?

> ..character sequence consisting of the characters number sign and exclamation mark (#!) at the beginning of a script...

<br/> **`#!interpreter [optional-arg]`**

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
## <span>Bad</span> or <span>dangerous</span> Shebangs</span> 🤷‍♀️
Some unfortunately very popular ones...
```css
#!/bin/sh
```
```css
#!/bin/bash
```
this works for others or with parameters too... and is also **bad**
```css
#!/usr/bin/python -c
```
<small>**`#!interpreter [optional-arg]`**</small>

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
## <span>Good</span> Shebangs 🤩
\- use these unless you have a good reason for doing otherwise - <!-- .element: class="subtitle" -->

```css
#!/usr/bin/env bash
```

```css
#!/usr/bin/env python -c
```

try this one!
```css
#!/usr/bin/env cat
```

<small>**`#!interpreter [optional-arg]`**</small>

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
## Bad Shebangs 🤦‍♀️

* **`#!/bin/bash`** is like running
```bash
$ /bin/bash
```

* **`#!/usr/bin/env bash`** is like running
```bash
$ bash
```

## 🆗 🆒
<br/>... but where is the Problem? Remember **`$PATH`**...!

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
## Bad Shebangs 🤦‍♀️

Which binary is run when just typing **`cat`** or **`bash`** without full path?

* **`#!/bin/bash`**
```bash
$ command -v /bin/bash
/bin/bash
```

* **`#!/usr/bin/env bash`**
```bash
$ command -v bash
/usr/local/bin/bash
```

**⚠️ ⚠️ DIFFERENT BINARIES ⚠️ ⚠️** <!-- .element: class="fragment" style="color: red; font-size: xxx-large;" -->

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
## Bad Shebangs 🤦‍♀️
Bash on macOS 10.14.4 (18E226)

* **`#!/bin/bash`**
```bash
$ /bin/bash --version
GNU bash, version 3.2.57(1)-release (x86_64-apple-darwin18)
Copyright (C) 2007 Free Software Foundation, Inc.
```

* **`#!/usr/bin/env bash`**
```bash
$ bash --version
GNU bash, version 5.0.7(1)-release (x86_64-apple-darwin18.5.0)
Copyright (C) 2019 Free Software Foundation, Inc.
```

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
## Bad Shebangs 🤦‍♀️
Python with multiple installed Version (`venv`, `pyenv`)

* **`#!/usr/bin/python`**
```bash
$ /usr/bin/python --version
Python 2.7.10
```

* **`#!/usr/bin/env python`**
```bash
$ python --version
Python 3.7.3
```

----

# Scripts

* put commands in a file, one per Line
* write a **`shebang`** in the first line of that file
* start with **`./script.sh`** (maybe you need permissions to execute something)

### <br/>Hello World!
```bash
#!/usr/bin/env bash

echo "Hello World, ${USER}!"
```

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
# ShellCheck
Shell script linter - available as package or via web

### <https://www.shellcheck.net>

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
# ShellCheck

```bash
#!/usr/bin/env bash
echo Hello World, ${USER}!
```
Linting results in
```bash
$ shellcheck helloworld.sh
In helloworld.sh line 3:
echo Hello World, ${USER}!
                  ^-- --^ SC2086: Double quote to prevent globbing and word splitting.
```

----

<!-- .slide: class="bulletpoints color-bulletpoints" -->
# ShellCheck

```bash
#!/usr/bin/env bash
echo "Hello World, ${USER}!"
```

```bash
$ shellcheck helloworld.sh
$
```
