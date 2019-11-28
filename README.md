<p align="center">
  <img src="docs/wordmark.svg?sanitize=true" alt="Fleck wordmark"><br/>
  Fleck is a Clojure-like LISP that runs wherever Bash is.
</p>

<p align="center"><img src="docs/screencast.svg?sanitize=true" alt="Fleck screencast"></p>

# Get it

```shell
curl -s https://chr15m.github.io/flk/flk > flk && chmod 755 flk
./flk
```

### [Examples](./examples) | [Reference](#reference) | [FAQ](#faq) | [make-a-lisp](https://github.com/kanaka/mal)

# What?

```
$ echo '(println "Hello world!") (println "Hostname:" (sh* "hostname")))' > example.clj
$ ./flk example.clj
Hello world!
Hostname: diziet
```

# Why?

Now you can use a humble LISP to do Bash things.
Bash as a scripting language has many edges, but it is everywhere.
Fleck attempts to round off the edges.

# How?

Almost all of this code is from the [make-a-LISP](https://github.com/kanaka/mal/) project. All I've done is put together a simple Makefile to package it up into an easily deployable single-file bash script.

# Reference

A list of macros and functions that are present in Fleck.

## Built-ins

This is the set of built-ins from the make-a-lisp project.
These more or less work but are generally more limited in functionality than their Clojure equivalents.
For example the addition function `(+)` can only add two numbers at a time.

`def!` | `defmacro!` | `if` | `do` | `fn*` | `try*` | `sh*` | `let*` | `quote` | `quasiquote` | `macroexpand` | `type` | `=` | `throw` | `nil?` | `true?` | `false?` | `string?` | `symbol` | `symbol?` | `keyword` | `keyword?` | `number?` | `fn?` | `macro?` | `pr-str` | `str` | `prn` | `println` | `readline` | `read-string` | `slurp` | `<` | `<=` | `>` | `>=` | `+` | `-` | `*` | `/` | `time-ms` | `list` | `list?` | `vector` | `vector?` | `hash-map` | `map?` | `assoc` | `dissoc` | `get` | `contains?` | `keys` | `vals` | `sequential?` | `cons` | `concat` | `nth` | `first` | `rest` | `empty?` | `count` | `apply` | `map` | `conj` | `seq` | `with-meta` | `meta` | `atom` | `atom?` | `deref` | `reset!` | `swap!`

## Extras

These functions are defined in Fleck itself or pulled in from the `mal/lib/` folder.

`pprint` | `str-replace` | `str-split`

 * `(str-replace STRING FIND REPLACE)` - Replace all occurrences of the string `FIND` in `STRING` with the string `REPLACE`.
 * `(str-split STRING SPLIT-CHARACTER)` - Split `STRING` into a list of strings on the single characters `SPLIT-CHARACTER`.

## Aliases

These are wrappers around the limited internal versions of the make-a-lisp macros and functions and are much more limited than the Clojure equivalents.

`let` | `when` | `def` | `fn` | `defn`

# FAQ

Think of this as homoiconic Bash rather than Clojure, and code as if you're in Bash.

### Will my favourite piece of Clojure run in this?

No, it's bash.

### Why can't I add more than 2 numbers together?

It's bash. Try invoking bc: `(sh* "bc <<< '1 + 2 + 3 + 4'")`

### Where are the floating point numbers?

It's bash. Try invoking bc: `(sh* "bc <<< '3 + 0.1415926'")`

### Why can't I iterate on a string?

It's bash. Try `(seq "somestring")`.

### How do I do destructuring?

You can't.

### Why is it called Fleck?

At 36k and running on any machine with Bash, the name seemed appropriate.

```
 fleck

    n. A tiny mark or spot.
    n. A small bit or flake.
```