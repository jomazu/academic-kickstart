---
# Course title, summary, and position.
linktitle: About Erlang and Elixir
summary: Why Erlang and Elixir.
weight: 2

# Page metadata.
title: Overview
date: "2019-10-01"
lastmod: "2020-07-07"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  elixir_fundamentals:
    name: Overview
    weight: 2
---

![Erlang logo](https://res.cloudinary.com/jomazu/image/upload/w_0.20,c_scale/v1571541788/jomazu/logos/Erlang_logo.png)

<br>

[Erlang](https://www.erlang.org/) is a general-purpose development platform for building scalable and reliable systems that constantly provide service with little or no downtime.

>Conceived in the mid-1980s by [Ericsson](https://www.ericsson.com/en/news/2018/5/erlang-celebrates-20-years-as-open-source), a Swedish telecom giant, Erlang was driven by the needs of the company's own telecom systems, where properties like reliability, responsiveness, scalability, and constant availability were imperative (Juric, 2019, p. 1). 

The development of Erlang was led by [Joe Armstrong](https://en.wikipedia.org/wiki/Joe_Armstrong_(programmer)), [Robert Virding](https://codesync.global/speaker/robert-virding/) and [Mike Williams](https://codesync.global/speaker/mike-williams/) at the Ericsson Computer Science Labs.

As mentioned, Erlang was specifically created to support the development of highly available systems - working 24/7 without any downtime. To do so, the system had to address the following challenges:

- `Fault-Tolerance` - keep working when something unforeseen happens.
- `Scalability` - handle any possible load, including the ability to respond to load increases by adding more hardware resources without any software intervention or a system restart.
- `Distribution` - scale horizontally by adding more machines without interruption.
- `Responsiveness` - always be reasonably fast and responsive.
- `Live update` - push new versions of software without restarting any servers.

Erlang provides the tools to address these challenges - that's what it was built for. 

<br>

---
<br>

## Erlang Concurrency
At the heart and soul of Erlang systems is concurrency, as illustrated in figure 1.1.

- `BEAM` - the Erlang virtual machine (VM), called BEAM (`B`ogdan/Bjorn's `E`rlang `A`bstract `M`achine).
- `Erlang process` - the basic concurrency primitive.
- `Schedulers` - what BEAM uses to distribute the execution of `processes` over the available CPU cores.

Concurrency promotes:

- `Fault-Tolerance`
  - Erlang *processes* are completely isolated from each other. They share no memory - a crash of one *process* doesn't cause a crash of other *processes*.
- `Scalability`
  - *Processes* communicate via asynchronous messages - beginning each message after finishing the preceding one.
  - Typical Erlang systems are divided into a large number of concurrent processes, which cooperate together to provide the complete service.
  - The VM can efficiently parallelize the execution of *processes* as much as possible. This makes Erlang systems scalable, because they can take advantage of all available CPU cores.
- `Distribution`
  - Communication between *processes* works the same way regardless of whether the *processes* reside in the same BEAM instance or on two different instances on two separate, remote computers.
- `Responsiveness`
  - Erlang takes the execution of multiple *processes* into its own hands by employing dedicated *schedulers* that interchangeably execute many Erlang *processes*.
  - A *scheduler* is preemtive - it gives a small execution window to each *process* and then pauses it and runs another *process*. Because the execution window is small, a single long-running *process* can't block the rest of the system.
  - I/O operations are internally delegated to separate threads. Any *process* that waits for an I/O operation to finish won't block the execution of other *processes*.

![Erlang Concurrency](https://res.cloudinary.com/jomazu/image/upload/w_0.30,c_scale/v1570048600/jomazu/BEAM_concurrency.png)

**Figure 1.1** Concurrency in the Erlang VM

<br> 

---
<br>

## Erlang - Server-Side Systems
Erlang can be used in various applications and systems, such as desktop applications and embedded environments. However, its sweet spot lies in **server-side systems** - systems that run on one or more servers and must serve many simultaneous clients. It is an entire system that does more than handle requests, run various background jobs, and manage server-wide in-memory state, as illustrated in figure 1.2.

A server-side system is often distributed on multiple machines that collaborate to produce **business value**.

![Server-side system](https://res.cloudinary.com/jomazu/image/upload/w_0.30,c_scale/v1570048607/jomazu/Erlang_server-side_system.png)

**Figure 1.2** Server-side system

<br> 

---
<br>

## References

Juric, S. (2019). Elixir in action (2nd ed.). Shelter Island, NY: Manning Publications.

