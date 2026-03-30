<div align="center">

```
 ███╗   ███╗ █████╗ ██╗██╗      ██████╗ ███████╗███╗   ██╗
 ████╗ ████║██╔══██╗██║██║     ██╔════╝ ██╔════╝████╗  ██║
 ██╔████╔██║███████║██║██║     ██║  ███╗█████╗  ██╔██╗ ██║
 ██║╚██╔╝██║██╔══██║██║██║     ██║   ██║██╔══╝  ██║╚██╗██║
 ██║ ╚═╝ ██║██║  ██║██║███████╗╚██████╔╝███████╗██║ ╚████║
 ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝╚══════╝ ╚═════╝ ╚══════╝╚═╝  ╚═══╝
```

**Gmail Alias Generator — exploit the dot trick, multiply your inbox**

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](LICENSE)
[![Made by](https://img.shields.io/badge/made%20by-rkixz-ff6b35?style=flat-square)](https://github.com/rkixz)
[![Zero deps](https://img.shields.io/badge/dependencies-zero-a855f7?style=flat-square)](#)

</div>

---

## what is this?

Gmail has a quirk — **it completely ignores dots in usernames.**

That means every single one of these lands in the exact same inbox:

```
yourname@gmail.com
y.ourname@gmail.com
yo.urname@gmail.com
your.name@gmail.com
y.o.u.r.n.a.m.e@gmail.com
```

**MailGen** exploits this to generate every possible dot-trick variant of your address — giving you hundreds of unique, working aliases with zero extra accounts.

---

## why use aliases?

- 🕵️ **Track who sells your data** — give each site a unique alias
- 📭 **Filter mail by alias** — auto-label newsletters, shopping, spam
- 🔒 **Keep your real address private** — never expose it again
- 🚫 **Block a site** — just filter its alias to trash
- ♾️ **Unlimited, free, forever** — no signups, no new accounts

---

## demo

```
====================================================
   MailGen — Gmail Alias Generator by rkixz
====================================================

  Enter your Gmail address: john@gmail.com
  → 4-character username · up to 8 dot variants possible

  How many aliases to generate? 5

  Generating aliases... done.

----------------------------------------------------
     1.  john@gmail.com
     2.  j.ohn@gmail.com
     3.  jo.hn@gmail.com
     4.  j.o.hn@gmail.com
     5.  joh.n@gmail.com
----------------------------------------------------
  Total: 5 alias(es) generated

  Save output to a .txt file? (y/n): y
  Enter filename (default: aliases.txt): john-aliases

  ✓  Saved to 'john-aliases.txt'

====================================================
  Done! All emails above deliver to your inbox.
====================================================
```

---

## how many aliases can I get?

The number of dot-trick variants grows **exponentially** with username length:

| Username length | Max aliases |
|:-:|:-:|
| 4 chars | 8 |
| 6 chars | 32 |
| 8 chars | 128 |
| 10 chars | 512 |
| 12 chars | 2,048 |
| 15 chars | 16,384 |

> **Formula:** `2^(n-1)` where `n` = number of characters in your username

---

## install & run

**No dependencies. No pip. Nothing to install.**

```bash
# clone the repo
git clone https://github.com/blaxkmiradev/mailgen.git
cd mailgen

# run it
python3 mailgen.py
```

Requires **Python 3.10+** — that's it.

---

## usage

```
python3 mailgen.py
```

You'll be prompted for:

1. **Your Gmail address** — e.g. `yourname@gmail.com`
2. **How many aliases** — enter any number (capped at max possible)
3. **Save to file?** — `y` to export as `.txt`, `n` to skip

Output file format:
```
Gmail Alias Generator — yourname@gmail.com
====================================================
   1. yourname@gmail.com
   2. y.ourname@gmail.com
   3. yo.urname@gmail.com
   ...
====================================================
Total: 50 alias(es)
```

---

## how it works

Gmail's servers strip dots before routing — `j.o.h.n` and `john` are identical to them. MailGen uses **binary enumeration** to place dots in every possible gap between characters:

```python
# for a 4-char name like "john":
# gaps: [j_o_h_n] → 3 gaps → 2³ = 8 combinations

john        # 000
j.ohn       # 100
jo.hn       # 010
j.o.hn      # 110
joh.n       # 001
j.oh.n      # 101
jo.h.n      # 011
j.o.h.n     # 111
```

Each combination is a valid, unique email address that delivers straight to your inbox.

---

## file structure

```
mailgen/
├── mailgen.py      # main script
├── README.md       # you are here
└── LICENSE         # MIT
```

---

## license

MIT — do whatever you want with it.

---

<div align="center">

made with ♥ by **[rkixz](https://github.com/blaxkmiradev)**

*if this helped you, drop a ⭐ — it means a lot*

</div>
