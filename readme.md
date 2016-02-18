> Transform AST from [glsl-parser](http://stack.gl/packages/#stackgl/glsl-parser) to js.

## Usage

[![npm install glsl-js](https://nodei.co/npm/glsl-js.png?mini=true)](https://npmjs.org/package/glsl-js/)

```js
var parse = require('glsl-parse/stream');
var tokenize = require('glsl-tokenize/stream')
var compile = require('glsl-js/stream');
var stdlib = require('glsl-stdlib/webgl');
var glslify = require('glslify');

tokenize(glslify('./source.glsl'))
.pipe(parse())
.pipe(compile(stdlib));
```

Source:
```glsl
precision mediump float;
attribute vec2 uv;
attribute vec4 color;
varying vec4 fColor;
uniform vec2 uScreenSize;

void main (void) {
	fColor = color;
	vec2 position = vec2(uv.x, -uv.y) * 1.0;
	position.x *= uScreenSize.y / uScreenSize.x;
	gl_Position = vec4(position, 0, 1);
}
```

Result:
```js
var uv;
var color;
var fColor;
var uScreenSize;

function main () {
	fColor = color;
	var position = [uv.x * 1.0, -uv.y * 1.0];
	position.x *= uScreenSize.y / uScreenSize.x;
	gl_Position = [position[0], position[1], 0, 1];
}
```

## API

_glsl-js_ can be used as a stream:

```js
TODO
```

, directly:

```js
```

, or as a compiler:

```js
```

## Related

> [fake-gl](https://npmjs.org/package/fake-gl) — webgl implementation in node.</br>
> [glsl-stdlib](https://npmjs.org/package/fake-gl) — webgl/opengl stdlib for node.</br>
> [glsl.js](https://npmjs.org/package/glsl) — glsl to asm.js by [@devongovett](https://github.com/devongovett) compiler built with [jison](https://npmjs.org/package/jison). Project is abandoned :(.</br>
> [glsl spec](https://www.opengl.org/documentation/glsl/) — openGL Shader Language specification.