# StrafeLab.jl
<p align="center">
  <img src="https://img.shields.io/badge/Julia-9558B2?style=for-the-badge&logo=julia&logoColor=white" alt="Julia">
  <img src="https://img.shields.io/badge/Flux.jl-389826?style=for-the-badge" alt="Flux.jl">
  <img src="https://img.shields.io/badge/Reinforcement_Learning-4063D8?style=for-the-badge" alt="Reinforcement Learning">
  <img src="https://img.shields.io/badge/Status-Experimental-CB3C33?style=for-the-badge" alt="Experimental">
</p>
<p align="center">
  <img
    src="https://cdn.momentum-mod.org/img/8a99fcb6-6657-4aae-8a51-f4a94e8cacc1-large.jpg"
    width="650"
    alt="Momentum Mod - bhop_pop"
  >
</p>

### Learning source engine movement

*An experiment in reinforcement learning, and high-skill movement.*

**Starting with bunny hopping in Momentum Mod. Later, generalize on all styles.**

---

## The idea

Bunnyhopping looks simple until you try to do it well. 
Speed depends on precisely timed inputs, air acceleration, camera movement, and a constant stream of tiny corrections. Players learn those interactions through practice, often without consciously calculating them.
It is technically a glitch in the source engine, but we learned to love it and its a popular technique in the speed running community.

**Can an agent learn to do the same?**

StrafeLab is a Julia-first research playground for training neural agents to acquire movement skills in physics-based first-person games.

The goal isn't to replay a recorded route or hard-code an optimal strafe sequence - thats cheating! We wish to investigate whether a policy can learn useful control strategies from experience
and adapt those strategies to unfamiliar maps, movement styles, and eventually different physics engines.

The first target is **Momentum Mod**, beginning with basic air strafing and bunny hopping. We hope to get at least 1 finished run on **bhop_eazy_v2**

## Aspirations :)

| Movement | Questions worth investigating |
|---|---|
| **Bunnyhopping / air strafing** | Can an agent learn to gain and preserve speed using mouse and keyboard input? How does the agent operate on unseen maps? |
| **Normal, HSW, and sideways strafing** | Can different movement strategies emerge, and can a policy learn when each is useful? |
| **Surf** | Can a trained controller adapt to ramp-based movement and route planning? |
| **DeFRaG / CPMA** | What transfers between related but distinct Quake-family movement physics? |
| **Rocket jumping** | Can the agent coordinate aiming, firing, and movement to learn weapon-assisted jumps? |

These are research directions, not implemented features. Sharing a genre or movement vocabulary doesn't guarantee that a policy will transfer between environments.

## How I want to approach it

The initial design is intentionally close to what a player sees and does.

- **Observe:** Use on-screen information rather than game state (momentum mod is closed source, so we will need all the visual data supplied by the HUD. Luckily they give us alot and we can program our own hud elements!).
- **Act:** Produce real time inputs, and react to observations.
- **Learn:** Start with reinforcement learning, with room to investigate demonstrations, curricula, and different policy architectures.
- **Measure:** Track speed, consistency, map completion, and performance on environments the agent hasn't trained on.
- **Compare:** Test whether skills learned on one map or movement discipline help on another.

The specific observation format, reward design, algorithms, and evaluation protocol are still open questions. Part of the project is finding out what actually works.
We probably will train on runs already on the leaderboards before letting our agent waffle for a few hours. Although it moght be interesting to watch why style emerges if we do not let it observe any human behavior.


---

**Special thanks to the julia clan and momentum mod devs :).**
