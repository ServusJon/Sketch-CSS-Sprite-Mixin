Sketch CSS Spriting Mixin (retina ready)
======================================

## CSS Spriting super easy!
### Supporting SCSS / LESS / STYLUS


1. Place all the Icons on an Artboard
2. Give them a name (no white-space), name the artboard (Export Setting )
3. Export the artboard in 1x and 2x in your "img/"-Folder
4. Fire the Plugin "Sketch CSS Sprite Mixin"
5. Paste the code in your project
6. Include the Mixins in your classes


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

$play-icon: 22px 20px '../img/sprite.png' -47px -10px;
$world-icon: 22px 22px '../img/sprite.png' -7px -9px;

$play-icon-2x: 22px 20px '../img/sprite@2x.png' -47px -10px;
$world-icon-2x: 22px 22px '../img/sprite@2x.png' -7px -9px;
$spritemapWidth: 77px;
```

## After that add Icons to a class:

```
.logo {
	…

	@include cssSprite($play-icon);

	@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
		@include cssRetinaSprite($play-icon-2x);
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