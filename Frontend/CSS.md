# Reading CSS

## Grids

https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids

## Resources

https://google.github.io/material-design-icons/
https://material.io/resources/icons/?style=baseline

## Less

* http://lesscss.org/
* http://css-tricks.com/sass-vs-less/
* http://stackoverflow.com/questions/8411066/less-vs-sass-vs
* http://www.smashingmagazine.com/2011/09/09/an-introduction-to-less-and-comparison-to-sass/
* http://css-tricks.com/resolution-specific-stylesheets/
* http://lesscss.org/features/
* https://medium.com/@crisnoble/using-new-less-plugins-with-your-build-process-571ef543166d
* http://www.w3.org/Style/Examples/007/center.en.html

### Gradient

http://www.css3factory.com/linear-gradients/#remove
http://jsfiddle.net/webtiki/aV4H6/
https://www.google.com.eg/webhp?sourceid=chrome-instant&ion=1&espv=2&es_th=1&ie=UTF-8#q=gradient+to+img
http://gradientfinder.com/
http://localhost:9000/#blog/Native-Guide-To-Egyptian-Software-and-IT-Industry-From-Developers-To-Companies.md
http://drupal.stackexchange.com/questions/76974/easy-way-to-add-a-transparent-gradient-to-a-header

### Coloring

* http://www.google.com/design/spec/style/color.html#color-color-palette
* http://www.colourlovers.com/palettes/new/all-time/meta?page=2
* http://color.hailpixel.com/#123621,FEFEFB,345E9D,
* https://medium.com/backchannel/etsy-ceo-how-net-neutrality-shaped-my-life-c6d53cdc79d2
* http://ethanschoonover.com/solarized
* http://www.creativebloq.com/colour/tools-colour-schemes-12121430

### Images

* [Anatomy of responsive images](https://jakearchibald.com/2015/anatomy-of-responsive-images/?utm_content=buffer4518a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)

# CSS

## Navigation

http://navnav.co/

## Web Tools

* http://bootsnipp.com/
* http://bootsnipp.com/resources#4

# Typography

http://www.smashingmagazine.com/2009/08/20/typographic-design-survey-best-practices-from-the-best-blogs/

# Fonts

[W3.org Main Reference](http://www.w3.org/TR/css3-fonts/#font-face-rule)
http://typecast.com/

## Google Fonts

http://typecast.com/preview/google/Inconsolata

```
<link rel="stylesheet" type="text/css" href="http://fonts.googleapis.com/css?family=Inconsolata|Indie+Flower">
```

## Local Fonts (@font-face)

### Simple

```
@font-face {
    font-family: 'YourFontName';
    src: url('http://domain.com/fonts/font.ttf'); 
}

.classname {
    font-family: 'YourFontName';
}
```

### Full Compatibility

```
@font-face {
font-family: 'MyWebFont';
src: url('webfont.eot'); /* IE9 Compat Modes */
src: url('webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
url('webfont.woff') format('woff'), /* Modern Browsers */
url('webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
url('webfont.svg#svgFontName') format('svg'); /* Legacy iOS */
}
```

### Google like

```
@font-face {
  font-family: 'Indie Flower';
  font-style: normal;
  font-weight: 400;
  src: local('Indie Flower'), local('IndieFlower'), url(http://fonts.gstatic.com/s/indieflower/v7/10JVD_humAd5zP2yrFqw6ugdm0LZdjqr5-oayXSOefg.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215, U+E0FF, U+EFFD, U+F000;
}
```

# Less

## Frameworks

* http://markdotto.com/bootstrap/

## Tutorials

* http://verekia.com/less-css/dont-read-less-css-tutorial-highly-addictive

## Tricks

* http://designshack.net/articles/css/10-less-css-examples-you-should-steal-for-your-projects/

## Buttons

* [Amazing Button tricks](http://www.sanwebe.com/2013/01/40-css-buttons-from-codepen)
* http://cssdeck.com/labs/google-buttons
* [cool button](http://codepen.io/impressivewebs/pen/GzqId)

# Transitions

* http://sarasoueidan.com/blog/navicon-transformicons/
* http://codepen.io/Hornebom/pen/clDsr

```
// effects
filter:grayscale(100%);
-webkit-filter: saturate(0%)grayscale(100%)brightness(0%)contrast(1000%);
filter:gray;
filter:grayscale(0%);
-webkit-filter: grayscale(0%)contrast(100%);
filter:none;
```

# M-IO

http://codyhouse.co/demo/vertical-fixed-navigation/index.html#0

