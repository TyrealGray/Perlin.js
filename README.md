# perlin.js
Javascript 2D Perlin &amp; Simplex noise functions forked from https://github.com/josephg/noisejs

---
This is a simple library for 2d & 3d perlin noise and simplex noise in
javascript. Noise is
[pretty](https://josephg.com/perlin/3/).

The library is pretty fast (10M queries / sec). But its still way slower than
using a shader. For example, if you try and update an entire screen's worth of
pixels, it'll be [slow](http://josephg.github.com/noisejs/demo3d.html).

The code is based on Stefan Gustavson's implementation. Do whatever you want
with it, etc.

## install
`$ npm install --save perlin.js`

## How to make noise:

```javascript
import Perlin from 'perlin.js';

Perlin.seed(Math.random());

for (var x = 0; x < canvas.width; x++) {
  for (var y = 0; y < canvas.height; y++) {
    // All Perlin functions return values in the range of -1 to 1.

    // Perlin.simplex2 and Perlin.perlin2 for 2d noise
    var value = Perlin.simplex2(x / 100, y / 100);
    // ... or Perlin.simplex3 and Perlin.perlin3:
    var value = Perlin.simplex3(x / 100, y / 100, time);

    image[x][y].r = Math.abs(value) * 256; // Or whatever. Open demo.html to see it used with canvas.
  }
}
```

The library exposes an object called `Perlin` with the following properties:

- **simplex2(x, y)**: 2D Simplex noise function
- **simplex3(x, y, z)**: 3D Simplex noise function
- **perlin2(x, y)**: 2D Perlin noise function
- **perlin3(x, y, z)**: 3D Perlin noise function
- **seed(val)**: Seed the noise functions. Only 65536 different seeds are supported. Use a float between 0 and 1 or an integer from 1 to 65536. 
