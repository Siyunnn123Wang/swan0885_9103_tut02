
# Quiz 8 — Design Research

## Part 1: _Imaging Technique Inspiration
**Pacita Abad’s _Wheels of Fortune_** informs a tactile, rhythmic “wheel” interface. I’ll carry over:  
1) **Radial repetition** using concentric circles;  
2) **Bead-like ring textures**;  
3) **High-contrast colors** that **move/disperse over time** (particleization).  
These map neatly to parametric drawing and modular classes, ready for interaction with `touch/mouse` and `video/hand` input.

> Goal: a **touchable wheel** that responds to swipes, pinches, and camera gestures—keeping Abad’s rhythmic ornament while adding embodied play.

**High-quality references (embedded):**  
![Original Artwork](https://artlogic-res.cloudinary.com/w_1200,c_limit,f_auto,fl_lossy,q_auto/artlogicstorage/pacitaabad/images/view/858010e9ae81a7e52bf615e35c22bafb/pacitaabad-prints-sugar-donuts-2003.jpg) 
![Color/Detail Style](https://d1hhug17qm51in.cloudfront.net/www-media/2023/11/06114146/05_Pacita-Abad_If-My-Friends-Could-See-Me-Now_1991-72dpi-765x1024.jpg)  
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
  https://p5js.org/reference/#group-Touch  
- **`touches[]` array** (multi-touch points):  
  https://p5js.org/reference/#/p5/touches  
- **Mouse input overview (Happy Coding)**:  
  https://happycoding.io/tutorials/p5js/input

### 2.Hand Tracking / Video Input
- **Camera input** — `createCapture(VIDEO)`:  
  https://p5js.org/reference/#/p5/createCapture  
- **ml5.js Handpose** (hand landmarks):  
  https://ml5js.org/reference/api-Handpose/  
- **ml5 / PoseNet intro (The Coding Train)**:  
  https://thecodingtrain.com/learning/ml5/intro  
- **Pixels & video track (The Coding Train)** (e.g., *Video Pixels*, *Motion Detection*):  
  https://thecodingtrain.com/pixels

### 3. Easing / Springs (smooth interaction)
- **Easing (Happy Coding)**:  
  https://happycoding.io/tutorials/p5js/animation/easing  
- **Spring Forces (The Coding Train)**:  
  https://thecodingtrain.com/challenges/96-spring-forces

### 4. Particleization (disperse / reassemble)
- **The Coding Train — Challenges directory** (search *particle system*, *flow field*, *fireworks*):  
  https://thecodingtrain.com/challenges  
- **Happy Coding — Particle systems** (concepts, examples):  
  https://happycoding.io/tutorials/p5js/animation/particle-systems  
- **p5.js Examples index** (search *particles* / *arrays*):  
  https://p5js.org/examples/

### 5. Circle Collisions
- **Collision detection (Happy Coding)** (circle-circle & boundaries concepts):  
  https://happycoding.io/tutorials/p5js/physics/collision-detection  
- **Collision-related challenges (The Coding Train)**:  
  https://thecodingtrain.com/challenges

---

## Interaction Flow (text diagram)
```text
[User Input]
  ├─ Click/Drag/Touch → angular velocity Δθ/Δt → easing/spring → Wheel.rotate()
  ├─ Handpose/Camera → wrist angle / local motion → Wheel.rotate()/recolor()
  ├─ Trigger “disperse/reassemble” → particles update positions/velocities (particleization)
  └─ Circle–circle collision → resolve overlap/bounce/layering
Render loop: update() → draw() (concentric dot rings; this quiz links external code only—no custom code here)
