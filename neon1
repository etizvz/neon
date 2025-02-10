let rays = [];

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  noCursor();
  blendMode(ADD);
  for (let i = 0; i < 50; i++) {
    rays.push({
      x: random(width),
      y: random(height),
      angle: random(TWO_PI),
      speed: random(0.5, 2),
      length: random(50, 200),
      colorShift: random(100, 255)
    });
  }
}

function draw() {
  background(0, 20);

  translate(width / 2, height / 2);
  rotate(sin(frameCount * 0.001) * PI);

  for (let i = 0; i < rays.length; i++) {
    let r = rays[i];

    r.x += cos(r.angle) * r.speed;
    r.y += sin(r.angle) * r.speed;

    let gradient = drawingContext.createLinearGradient(r.x, r.y, r.x + r.length, r.y + r.length);
    gradient.addColorStop(0, `rgba(${r.colorShift}, 0, 255, 0.8)`);
    gradient.addColorStop(1, `rgba(255, 255, 255, 0.2)`);

    drawingContext.strokeStyle = gradient;
    strokeWeight(2);
    line(r.x, r.y, r.x + cos(r.angle) * r.length, r.y + sin(r.angle) * r.length);

    r.angle += random(-0.02, 0.02);

    if (r.x > width || r.x < -width || r.y > height || r.y < -height) {
      r.x = random(-width / 2, width / 2);
      r.y = random(-height / 2, height / 2);
      r.angle = random(TWO_PI);
    }
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
