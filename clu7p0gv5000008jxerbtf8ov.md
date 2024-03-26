---
title: "Designing Interactive Cosmic Phenomenon with  P5.js Simulations"
datePublished: Tue Mar 26 2024 01:23:11 GMT+0000 (Coordinated Universal Time)
cuid: clu7p0gv5000008jxerbtf8ov
slug: designing-interactive-cosmic-phenomenon-with-p5js-simulations
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711416105168/e2478a1f-fe80-4b98-991e-d2af55d4e21b.webp
tags: p5js, physics, creative-coding, gravity, educational-resource, gravitational-lensing

---

Hello there! If you ever peek into my world, you'll likely catch the sounds of the [Star Talk podcast](https://www.youtube.com/c/StarTalk), my constant companion, filling the air with tales of celestial wonders.

Have you ever looked up at the night sky and felt a sense of awe at the vastness of space? That's exactly what sparks my imagination every single day. I find myself captivated by the "dance of the stars", the distant twinkle of galaxies, and the magnificent ballet of planets. But, I wanted to do more than just gaze and wonder. I yearned to dive deeper, to interact with these cosmic phenomena in a way that's tangible, almost touchable.

That's where [p5.js](https://p5js.org/) comes into the picture–– a user-friendly coding platform that allows dreamers like me to bring our imaginations to life. Think of p5.js as a magic paintbrush, one that paints not just pictures but whole universes. With a few strokes of code, anyone can create simulations of the very cosmic activities that captivate me––although basic knowledge of the software are required. It's like having a personal universe on my computer screen, where I can play with the laws of physics, bend light, and explore the unknowns of space.

Through this blog, I invite you on an extraordinary journey. It's not just for the scientists with their PhDs or the experts with their telescopes. This is for anyone and everyone who's ever looked up at the sky and felt that stir of curiosity.

---

Now, let's turn our gaze to the remarkable phenomenon that we're going to explore through our p5.js simulations: gravitational lensing. This cosmic event is a fascinating and visually stunning manifestation of Einstein's theory of general relativity (Cunha & Herdeiro, 2018; Perlick, 2004). In simple terms, gravitational lensing occurs when the gravity of a massive object, like a galaxy or a black hole, bends the path of light from a more distant object (see Biesiada & Harikumar, 2021). It's like looking through a cosmic lens, where massive celestial bodies act as natural magnifying glasses, warping and amplifying the light from distant stars and galaxies.

I've asked Claude to explain gravitational lensing like ELI5: `"Imagine you're holding a magnifying glass, bending the light to see an ant appear bigger. Now, picture a massive galaxy doing the same thing, but with the light from an entire star system billions of miles away! This effect not only lets us see into the deeper realms of space but also helps astronomers study the distribution of dark matter, the nature of galaxies, and the expansion of the universe itself."`

With p5.js, we're going to bring this cosmic ballet to any screen, allowing us to visualize and interact with this phenomenon in a way that's both educational and mesmerizing.

When you **click and hold** in this sim, you are effectively creating a gravitational lensing scenario (really barebones for now) where light is being bent around a massive celestial body. This interactivity not only makes the concept of gravitational lensing more tangible but also visually demonstrates one of the intriguing predictions of Einstein's theory of general relativity.

### Gravitational Lensing Simulation (click and hold)

<iframe src="https://editor.p5js.org/saigattupalli/full/wbyfcNS55" style="width:100%;height:500px"></iframe>

Let me explain the inner workings of this code.

### For User Interactions:

```javascript
function setup() {
  createCanvas(800, 600);
  resetParticles();
}

function draw() {
  background(0);
  // ... [rest of the draw function]
}

function mousePressed() {
  attractorActive = true;
}

function mouseReleased() {
  attractorActive = false;
  resetParticles();
}

function resetParticles() {
  // ... [initialization of lightParticles]
}
```

This part of the code sets up the canvas and initializes the simulation. The *setup()* function creates a canvas and calls *resetParticles()* to populate it with light particles. The *draw()* function, which runs continuously, updates the display. It checks if the attractor (simulating a massive object causing gravitational lensing) is active and updates the particles accordingly. The activation of the attractor is controlled by mouse interactions, defined in *mousePressed()* and *mouseReleased()*. This interactive element demonstrates how gravitational lensing is influenced by the position and movement of massive objects in space, making it a practical educational tool for illustrating these concepts.

### Particle Dynamics:

```javascript
class LightParticle {
  // ... [constructor and attract method]
  
  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0); 
  }

  display() {
    // ... [visual representation of particles]
  }
}
```

The LightParticle class represents the individual light particles affected by gravitational lensing. Each particle has properties like position, velocity, and acceleration, crucial concepts in physics. The *update()* method applies Newtonian mechanics, updating the particle's motion based on its acceleration and velocity. The *display()* method visually represents each particle, making the simulation visually engaging and helping to convey the complex idea of how light is influenced by gravity.

### Simulating Gravitational Attraction:

```javascript
  attract(point) {
    let force = p5.Vector.sub(point, this.position);
    let distanceSq = constrain(force.magSq(), 100, 500); 
    let G = 2; // Gravitational constant
    let strength = G / distanceSq;
    force.setMag(strength);
    this.acceleration.add(force);
  }
```

This function within the LightParticle class is key to simulating gravitational lensing. It calculates the gravitational attraction between the light particle and the attractor (simulated by the mouse position). The force is inversely proportional to the square of the distance between the particle and the attractor, reflecting the principles of Newton's Law of Universal Gravitation. This function demonstrates how gravitational force influences light paths, a fundamental aspect of gravitational lensing. This aspect of the simulation offers a valuable, hands-on experience for understanding how massive objects in the universe can warp the path of light, an essential concept in astrophysics and general relativity.

Check out full sim here, including many other sims:

[https://editor.p5js.org/saigattupalli/collections/p8RTKTcdx](https://editor.p5js.org/saigattupalli/collections/p8RTKTcdx)

### Full code:

```javascript
let lightParticles = [];
let attractor;
let attractorActive = false;

function setup() {
  createCanvas(800, 600);
  resetParticles();
}

function draw() {
  background(0);

  if (attractorActive) {
    attractor = createVector(mouseX, mouseY);
    lightParticles.forEach(particle => {
      particle.attract(attractor);
      particle.update();
      particle.display();
    });
  } else {
    lightParticles.forEach(particle => {
      particle.update();
      particle.display();
    });
  }
}

function mousePressed() {
  attractorActive = true;
}

function mouseReleased() {
  attractorActive = false;
  resetParticles();
}

function resetParticles() {
  lightParticles = [];
  for (let i = 0; i < 100; i++) {
    lightParticles.push(new LightParticle(random(width), random(height)));
  }
}

class LightParticle {
  constructor(x, y) {
    this.originalPosition = createVector(x, y);
    this.position = this.originalPosition.copy();
    this.velocity = createVector();
    this.acceleration = createVector();
  }

  attract(point) {
    let force = p5.Vector.sub(point, this.position);
    let distanceSq = constrain(force.magSq(), 100, 500); 
    let G = 2; // Gravitational constant
    let strength = G / distanceSq;
    force.setMag(strength);
    this.acceleration.add(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0); 
  }

  display() {
    stroke(255, 100);
    strokeWeight(2);
    point(this.position.x, this.position.y);
  }
}
```

Until next time.

Cover image source: [Space.com](https://www.space.com/gravitational-lensing-explained)

### References

Biesiada, M., & Harikumar, S. (2021). Gravitational lensing of continuous gravitational waves. Universe, 7(12), 502.

Cunha, P. V., & Herdeiro, C. A. (2018). Shadows and strong gravitational lensing: a brief review. General Relativity and Gravitation, 50, 1-27.

Perlick, V. (2004). Gravitational lensing from a spacetime perspective. *Living reviews in relativity*, *7*, 1-117.