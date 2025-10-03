
# Quiz 8 — Design Research

## Part 1: _Imaging Technique Inspiration
**teamLab’s _Memory of Topography_** is a shin-high field of lily-like pads that glow and **react to bodies** moving through them. Scenes **cycle across seasons**—summer rice terraces, **firefly particles**, and cherry-blossom dispersals—flowing over mirrored water. I’ll carry over:  
1) **Radial/repeated pads** as modular circles;  
2) **Bead-like light dots** and **particle swarms** for fireflies/blossoms;  
3) **High-contrast palettes** that shift with presence and time.  
This fits the brief: parametric pads + particle layers + input mapping yield a rhythmic, touchable surface with immediate feedback.

These map neatly to parametric drawing and modular classes, ready for interaction with `touch/mouse` and `video/hand` input.

> Goal: a **touchable wheel** that responds to swipes, pinches, and camera gestures—keeping Abad’s rhythmic ornament while adding embodied play.

**High-quality references (embedded):**  
![Original Artwork](https://artlogic-res.cloudinary.com/w_1200,c_limit,f_auto,fl_lossy,q_auto/artlogicstorage/pacitaabad/images/view/858010e9ae81a7e52bf615e35c22bafb/pacitaabad-prints-sugar-donuts-2003.jpg) 
![Color/Detail Style](https://images.squarespace-cdn.com/content/v1/5d91f0811b06bc4c5b873679/1571499273479-L2XYV28KC0T1UDR3CNGF/20191018_234114.jpg?format=1000w)  
![Interaction/Installation view](https://images.squarespace-cdn.com/content/v1/5d91f0811b06bc4c5b873679/1571492391091-1Z8JAA9ZPLLE7WBUYVV5/20191018_222551.jpg?format=1500w)

---

## Part 2: _Coding Technique Exploration
No custom code—only **existing online examples**:  
1) **Mouse/Touch** (click, drag, swipe);  
2) **Hand tracking** (`ml5.js` Handpose / PoseNet);  
3) **Easing/Springs** for inertia;  
4) **Particleization**: dots disperse/reassemble, positions update over time;  
5) **Circle collisions** (overlap/response).  
These resources combine to realize the interactive, radial, dotted aesthetic from Part 1.

---

## Tutorial Index

### 1. Mouse / Touch
- **p5 Touch events** — `touchStarted()`, `touchMoved()`, `touchEnded()` (multi-touch):  
  - [`touchMoved()`](https://p5js.org/reference/p5/touchMoved/)
  - [`touchEnded()`](https://p5js.org/reference/p5/touchEnded/)
  - [`touchStarted()`](https://p5js.org/reference/p5/touchStarted/)
- **`touches[]` array** (multi-touch points):  
  - [`touches[]`](https://p5js.org/reference/p5/touches/)

### 2. Hand Tracking / Video Input
- **Camera input** — `createCapture(VIDEO)`:  
  - [`createCapture(VIDEO)`](https://p5js.org/reference/p5/createCapture/)
- **Pixels & video track (The Coding Train)** (e.g., *Video Pixels*, *Motion Detection*):  
  - [Pixels & Video track](https://thecodingtrain.com/pixels)

### 4. Particleization (disperse / reassemble)
- **The Coding Train — Challenges directory** (search *particle system*, *flow field*, *fireworks*):  
  - [Challenges directory](https://thecodingtrain.com/challenges)
- **p5.js Examples index** (*particles*):  
  - [p5.js particles](https://p5js.org/examples/classes-and-objects-connected-particles/)

### 5. Circle Collisions
- **Collision-related challenges (The Coding Train)**:  
  - [Collision challenges](https://editor.p5js.org/codingtrain/sketches/3DrBb8LCp)


---

## Interaction Flow (text diagram)
```text
[User Input]
  ├─ Click/Drag/Touch → angular velocity Δθ/Δt → easing/spring → Wheel.rotate()
  ├─ Handpose/Camera → wrist angle / local motion → Wheel.rotate()/recolor()
  ├─ Trigger “disperse/reassemble” → particles update positions/velocities (particleization)
  └─ Circle–circle collision → resolve overlap/bounce/layering
Render loop: update() → draw() (concentric dot rings; this quiz links external code only—no custom code here)
