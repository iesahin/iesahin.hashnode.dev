---
title: "bits 4"
datePublished: Tue Mar 14 2023 11:19:00 GMT+0000 (Coordinated Universal Time)
cuid: clfdo3kuu015ssqnv0vy60dsk
slug: bits-4
canonical: https://emresahin.net/bits-4/

---

I want to use channels for Xvc pipelines. A thread will be created for each step and will get dependency state changes via channels.

Note that the number of dependencies is arbitrary. There may be thousands of dependencies, e.g., files for a step and creating these channels beforehand is not feasible.

Crossbeam library has [Select](https://docs.rs/crossbeam/latest/crossbeam/channel/struct.Select.html#) that allows to wait for arbitrary number of channels. Now, I need to figure out how to structure the threads and update their states. A minor task 😆