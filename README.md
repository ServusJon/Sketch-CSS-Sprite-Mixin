Sketch CSS Sprite Mixin (retina ready)
======================================

Generate a code of mixin for scss, less and stylus in Sketch 3. Code is copied to the clipboard when run the plugin.

Sprites name are group layer name of top-level, and the Sprite image name is an Artboard name.

![Screen Shot](http://s4.postimg.org/gsit6dnod/Bildschirmfoto_2015_01_09_um_15_21_07.png)

Copy this code on top in your CSS:

**SCSS**

```scss
@mixin cssSprite( $spriteVals ) {
	width: nth( $spriteVals, 1 );
	height: nth( $spriteVals, 2 );
	background-repeat: no-repeat;
	background-image: url( #{ nth( $spriteVals, 3 ) } );
	background-position: nth( $spriteVals, 4 ) nth( $spriteVals, 5 );
}

@mixin cssRetinaSprite( $spriteVals ) {
	width: nth( $spriteVals, 1 );
	height: nth( $spriteVals, 2 );
	background-repeat: no-repeat;
	background-image: url( #{ nth( $spriteVals, 3 ) } );
	background-position: nth( $spriteVals, 4 ) nth( $spriteVals, 5 );
	background-size: 77px auto;
}

$play-icon: 22px 20px '../img/Artboard 1.png' -47px -10px;
$world-icon: 22px 22px '../img/Artboard 1.png' -7px -9px;

$play-icon-2x: 22px 20px '../img/Artboard 1@2x.png' -47px -10px;
$world-icon-2x: 22px 22px '../img/Artboard 1@2x.png' -7px -9px;
$spritemapWidth: 77px;
```

**LESS**

```less
.cssSprite( @spriteVals ) {
	width: extract( @spriteVals, 1 );
	height: extract( @spriteVals, 2 );
	background-repeat: no-repeat;
	background-image: e(%('url(%s)', extract( @spriteVals, 3 ) ) );
	background-position: extract( @spriteVals, 4 ) extract( @spriteVals, 5 );
}

.cssRetinaSprite( @spriteVals ) {
	width: extract( @spriteVals, 1 );
	height: extract( @spriteVals, 2 );
	background-repeat: no-repeat;
	background-image: e(%('url(%s)', extract( @spriteVals, 3 ) ) );
	background-position: extract( @spriteVals, 4 ) extract( @spriteVals, 5 );
	background-size: 77px auto;
}

@play-icon: 22px 20px '../img/Artboard 1.png' -47px -10px;
@world-icon: 22px 22px '../img/Artboard 1.png' -7px -9px;

@play-icon-2x: 22px 20px '../img/Artboard 1@2x.png' -47px -10px;
@world-icon-2x: 22px 22px '../img/Artboard 1@2x.png' -7px -9px;
@spritemapWidth: 77px;
```

**Stylus**

```stylus
cssSprite( $spriteVals )
	width: $spriteVals[0];
	height: $spriteVals[1];
	background-repeat: no-repeat;
	background-image: url( $spriteVals[2] );
	background-position: $spriteVals[3] $spriteVals[4];


cssRetinaSprite( $spriteVals )
	width: $spriteVals[1];
	height: $spriteVals[2];
	background-repeat: no-repeat;
	background-image: url( $spriteVals[3] );
	background-position: $spriteVals[4] $spriteVals[5];
	background-size: 77px auto;


$play-icon = 22px 20px '../img/Artboard 1.png' -47px -10px;
$world-icon = 22px 22px '../img/Artboard 1.png' -7px -9px;

$play-icon-2x = 22px 20px '../img/Artboard 1@2x.png' -47px -10px;
$world-icon-2x = 22px 22px '../img/Artboard 1@2x.png' -7px -9px;
$spritemapWidth: 77px;
```

**After that add Icons to a class:**

```
.logo {
	…

	.cssSprite( $play-icon );

	@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
    .cssRetinaSprite( $play-icon-2x );
  }
}
```


## License

The MIT License (MIT)

(c) 2014

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.