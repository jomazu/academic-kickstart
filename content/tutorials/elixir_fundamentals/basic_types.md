---
title: Basic Types
linktitle: Basic Types
toc: true
type: docs
date: "2020-07-07"
lastmod: "2020-07-07"
draft: false
menu:
  elixir_fundamentals:
    parent: Elixir
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---
---
<br>

## Interactive Elixir
To start an interactive Elixir session, type `iex` at the command prompt.

To exit IEx, type either:  

* `Ctrl + c` (twice)
* `Ctrl + \` (once)

---
<br>

## IEx Helpers
Once in the IEx session, type `h`, then hit `return` to view documentation for the module `IEx.Helpers`.

Try running the following from IEx:

```ruby
# Help on Functions handling input/output (IO)
iex(1)> h IO

# Print VM/runtime info for memory usage
iex(2)> runtime_info :memory
```
<br>

---
<br>

## Basic Data Types
* Atom ( `h Atom` )
  * Boolean
  * Nil
* Integer ( `h Integer` )
* Float ( `h Float` )
  * Scientific Notation
* String ( `h String` )
  * Concatenation
  * Interpolation
  * Strings are Binary
* Charlist
---
<br>

## Atom
An atom is a literal, a constant with name. It is a constant whose name is its value. Atoms are very useful for pattern matching.

```ruby
:my_atom
:testing
:customer_type
```

An atom begins with a **colon** and typically is all lowercase using an underscore to separate words.

Atoms are stored in the "atom table".

**NOTE:** Preventing Denial-of-Service attacks. 

Atoms are not garbage collected. The important thing to learn from this is you should not allow user provided content to become an atom at runtime in your system.

Converting unchecked user data to an atom can expose your system to a [Denial-of-Service (DOS) attack](https://en.wikipedia.org/wiki/Denial-of-service_attack).

This is how the attack works: a malicious actor causes your system to repeatedly create unique atoms until it consumes all of the available resources on your machine, causing it to crash. It is not a security flaw or "break-in", but can be abused to cause your system to crash.

---
<br>

## Boolean
The booleans `true` and `false` are implemented as special reserved atoms.

Elixir allows you to skip the leading `:` for the atoms `true` and `false`.

---
<br>

## Nil
Nil represents the absence of a value. Nil is implemented as a special reserved atom.

In evaluations, `nil` behaves like `false`.

Elixir allows you to skip the leading `:` for the atom `nil`.

---
<br>

## Integer
Represents positive and negative whole numbers, including zero.

Integers can be represented as a Hex and more...
```ruby
# Hex example
iex(1)> 0xFF
=> 255

# Grouping example
iex(2)> 1_000_000
=> 1000000
```
<br>

---
<br>

## Float
Represents floating point numbers.

Floats do not support a "Decimal" type for explicit levels of precision. Thus, it results in typical floating point rounding issues.

```ruby
iex(1)> 0.8 * 3
=> 2.4000000000000004
```

This is expected with floating point math. Refer to the following links:

* [Floating Point Math](http://0.30000000000000004.com/)
* [What Every Programmer Should Know About Floating-Point Arithmetic](https://floating-point-gui.de/)

If you need to represent fixed decimal values for something like money, using a Float may not be the most appropriate choice. For example, it may work better to use an integer that represents cents (instead of whole dollars).

Another option is to use a package called [Decimal](https://hex.pm/packages/decimal) that provides arbitrary precision.

---
<br>

## Scientific Notation
Floats are frequently displayed in their scientific notation. This may not be what you expect or want.

```ruby
iex(1)> 5600.0
=> 5.6e3
```

Note, that when working in IEx, it converts the data to a string for display in the shell. This is the same display as `Float.to_string/1`.

```ruby
iex(1)> Float.to_string(5600.0)
=> "5.6e3"
```

If you need to convert a float to a string with explicit decimal precision, use the built-in Erlang function `float_to_binary`. In Elixir, you can use any Erlang function. In the example below, the function we want is declared in the `erlang` module. To call it, use an atom as the module name like this:

```ruby
iex(1)> :erlang.float_to_binary(5600.0, decimals: 2)
=> "5600.00"
```
<br>

---
<br>

## String
Strings are encoded in [UTF-8](https://home.unicode.org/). A string uses the double quote character `"`. Single quoted text is not a string, that's a `charlist` and behaves differently.

```ruby
iex(1)> String.upcase("hello elixir")
=> "HELLO ELIXIR"
```
<br>

---
<br>

## Concatenation
Elixir strings can be concatenated using the `<>` operator.

```ruby
iex(1)> "One" <> ", Two"
=> "One, Two"

iex(2)> text = "Hello"
=> "Hello"
iex(3)> text <> " World!"
=> "Hello World!"
```
<br>

---
<br>

## Interpolation
Elixir strings support interpolation using the `#{...}` characters embedded in a string.

```ruby
iex(1)> name = "John"
=> "John"
iex(2)> "Hey #{name}!"
=> "Hey John!"
```

<br>

---
<br>

## Strings are Binary
[UTF-8](https://home.unicode.org/) strings did not exist in Erlang prior to Elixir. Because of this, many Erlang functions that take a string don't take an Elixir string. Erlang sees an Elixir string as a `binary` type.

```ruby
iex(1)> is_binary("A string")
=> true
```
In Erlang, functions often expect a `charlist`.

---
<br>

## Charlist
Mostly used for interoperability with Erlang. It is just a list of code points and is created with single quotes.

```ruby
iex(1)> 'This is a charlist'
=> 'This is a charlist'
iex(2)> is_list('testing')
=> true
```

A `charlist` can be converted to a string and vice versa using these functions:

* `Kernel.to_string/1`
* `Kernel.to_charlist/1`

**Kernel** is Elixir's default environment. It even defines basic math operators like `+` and `-`. Because it is so essential to Elixir, the [Kernel module](https://hexdocs.pm/elixir/Kernel.html) is always included for you. You can use the functions `to_string/1` and `to_charlist/1` to convert between the types without needing to specify the "Kernel" module explicitly.

```ruby
iex(1)> to_string('hello world')
=> "hello world"
iex(2)> to_charlist("hello world")
=> 'hello world'
```
<br>

---
<br>

## Modules to Manipulate
All of the types above are primitives, they are "data". They are **not objects** with functions attached to them. 

There are **no "objects"** in Elixir. There is only "data" and "functions". Modules are a collection or a container for functions.

By convention, when you want to perform some function on a piece of data, you use the type's module for doing that. This is particularly the case for Atom, Integer, Float, and String.

---
