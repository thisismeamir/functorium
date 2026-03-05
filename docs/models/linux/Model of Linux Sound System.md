Any Linux sound system consists of several layers:

- Drivers and low-level interfaces — hardware support and control.
- [User-mode](https://en.wikipedia.org/wiki/Protection_ring "wikipedia:Protection ring") API (libraries) — utilized and required by applications.
- User-mode sound servers **(optional)** — best for the complex desktop, needed for multiple simultaneous audio applications, and vital for more advanced capabilities, e.g. [pro audio](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Pro_audio "Pro audio").
- Sound frameworks **(optional)** — higher-level application environments not involving server processes.

In this model we investigate sound in Linux based operating systems, specially for advanced cases such as music production and DAWs as well.

- [[Advanced Linux Sound Architecture (ALSA)]]