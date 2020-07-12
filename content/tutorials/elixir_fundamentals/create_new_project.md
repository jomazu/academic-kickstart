---
title: Create a New Project
linktitle: Create a New Project
toc: true
type: docs
date: 2020-07-08T12:57:49-07:00
lastmod: 2020-07-08T12:57:49-07:00
draft: false
menu:
  elixir_fundamentals:
    parent: Elixir
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---


## New Project
Create a new Elixir project using.

```ini
$ mix new (project_name)
$ cd (project_name)
$ tree
```

The file `mix.exs` defines the configuration of your project. The source code lives under `lib/`.

While in the top-level directory of the application (the one containing the `mix.exs` file), use this command to compile the application.

```ini
$ mix
```

Some helpful options and commands to use from the command prompt:

* `mix help`
* `mix help run`
* `iex -h`
* `elixir -h`

