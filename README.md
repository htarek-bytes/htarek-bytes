<h1 align="center">Tarik Hireche</h1>

<p align="center">
  Bilingual Software Developer | Java, C#, SQL, Cloud & Infrastructure<br>
</p>

<p align="center">
  <a href="https://htarek.systems">Portfolio</a> ·
  <a href="https://htarek.systems/resume_htarek.pdf">Résumé</a> ·
  <a href="mailto:tarik.hireche@umontreal.ca">tarik.hireche@umontreal.ca</a>
</p>

---

## About

I like understanding the layer underneath the one I'm working in: the syscalls under a
process supervisor, the allocator under a language runtime, the register writes under a
sensor driver. Most of what I publish comes out of that: small, finished projects that go
deep on one mechanism rather than wide across many.

I care about the parts that make code usable by other people: tests, CI, a README that
explains the problem before the solution, and a build that works on a machine that isn't mine.

**Currently:** building an ESP32-S3 environmental data logger (bare-metal I2C driver for the
BME280, FreeRTOS task decomposition, ring buffer over flash) and going deeper on RTOS
scheduling and electronics.

## Projects

### [sentinel](https://github.com/htarek-bytes/sentinel): process supervisor for Linux containers
`C++17` · `CMake` · `Docker` · `Prometheus` · `Grafana` · `GitHub Actions`

A PID 1 init for containers, built from the syscall level up. Handles the problems `tini` and
`dumb-init` exist to solve: forwarding signals to the child's process group, reaping orphaned
descendants, escalating to SIGKILL after a grace period, and propagating the child's exit status
so it composes with shell scripts and CI. Adds supervised restarts with exponential backoff and a
Prometheus metrics endpoint. Ships as a two-stage container image with a Compose stack
(Prometheus + Grafana, alert rules provisioned), and CI brings that whole stack up on every push.
The build fails unless the target scrapes, the counters move, and the dashboard serves.

### [zig-custom-allocators](https://github.com/htarek-bytes/zig-custom-allocators): memory allocators from scratch
`Zig` · `std.testing`

Three allocators built against Zig's `std.mem.Allocator` interface, each adding a capability the
previous one lacks: a bump allocator, a tagged allocator with a per-block header, and a recycling
first-fit allocator that reuses freed blocks. Each plugs into the standard vtable, so ordinary Zig
code runs against them unmodified, and each ships its own test suite covering alignment, buffer
exhaustion, and block reuse. The README documents an alignment bug that passed on x86-64 and
panicked on ARM, and why aligning an offset instead of an absolute address causes it.


## Skills

- **Languages:**Java, C#, Python, SQL
- **Systems:** Linux, POSIX/syscalls, concurrency & synchronisation, memory management
- - **Tooling:** Git, CMake, Docker & Compose, GitHub Actions, PostgreSQL, Prometheus, Grafana, Neovim

## Education

**B.Sc. Computer Science, Université de Montréal**

Coursework in operating systems, algorithms & data structures, computer architecture, software
engineering, databases, and artificial intelligence.

I also keep my study notes public, since writing something down is how I find out whether I
actually understand it:
[electricity](https://github.com/htarek-bytes/My-notes/blob/main/Electricity/Coulomb_Voltage_Current_Watts.pdf) ·
[operating systems](https://github.com/htarek-bytes/My-notes/blob/main/2245_OS/OS_1.pdf)

## Contact

- **Email:** tarik.hireche@umontreal.ca
- **Portfolio:** [htarek.systems](https://htarek.systems)
- **Résumé:** [htarek.systems/resume_htarek.pdf](https://htarek.systems/resume_htarek.pdf)
