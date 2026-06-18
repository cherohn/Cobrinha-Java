# Cobrinha — Snake Game in Java

A classic Snake game built with Java Swing, featuring sound effects, a threaded game loop, and input synchronization via `Semaphore`.

---

## Features

- Smooth game loop running on a dedicated thread
- Keyboard input handling (arrow keys) with direction-change validation
- Sound effects on eating and game over (Java Sound API)
- Score tracking and game over screen
- Custom food image rendered via `Graphics`

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 21 |
| UI | Swing / AWT (`JFrame`, `JPanel`, `Graphics`) |
| Audio | Java Sound API (WAV) |
| Concurrency | `Thread` + `Semaphore` for game loop / input sync |
| Build | IntelliJ IDEA (no Maven/Gradle) |

---

## Architecture

```
Principal.java         → Entry point, creates window and starts game thread
Jogo.java             → Game loop (Runnable), state updates, rendering
Cobrinha.java         → Snake logic: movement, growth, collision detection
Comida.java           → Food position generation and rendering
InterrupcaoTeclado.java → Keyboard listener, direction changes
```

One non-obvious detail: direction changes from keyboard input run on the AWT event thread, while the game loop runs on a separate thread. A `Semaphore` coordinates access to shared state between them — which is why the game doesn't glitch when you rapidly change direction.

---

## Running Locally

**Requirements:** Java 21+, IntelliJ IDEA (or any IDE)

```bash
git clone https://github.com/cherohn/Cobrinha-Java.git
```

Open in IntelliJ → Run `Principal.java`.

---

## Author

**Matheus Garcez** — [github.com/cherohn](https://github.com/cherohn)
