# Web development
List of resources for web development

## Markdown
* [Cos'è il markdown](#cosè-il-markdown) 

## CSS
* [CSS Guideslines](#css-gudelines)

## Design

* [Full Screen Navigation Overlay](#full-screen-navigation-overlay) 
* [Off Canvas Navigation](#off-canvas-navigation) 
* [Responsive Dropdown Navigation Bar](#responsive-dropdown-navigation-bar)
* [Flexbox Grid](#flexbox-grid)
* [Float Grid](#float-grid)


## Cos'è il markdown
Il Markdown è un linguaggio di formattazione creato da John Gruber e Aaron Swartz che consente di comporre testi velocemente con una sintassi semplice ed efficace.
Esso permette di inserire titoli, link, elenchi e altri stili utilizzando caratteri regolari e segni di punteggiatura.
I testi possono poi essere convertiti in HTML immediatamente fruibile senza la paura di dimenticare la chiusura di tag o fare errori di scrittura di tag HTML
Il grosso vantaggio del Markdown è quello di generare dei file di testo che contengono la formattazione.
I nostri file diventano così multipiattaforma: possono essere aperti con qualsiasi applicazione e su qualsiasi piattaforma senza perdere le formattazioni applicate al testo.

Per la sintassi fare riferimento a [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) 

Ed ecco il [markdown supportato da wordpress](https://en.support.wordpress.com/markdown-quick-reference/)

## CSS Gudelines
High-level advice and [guidelines](https://cssguidelin.es/) for writing sane, manageable, scalable CSS

## Full Screen Navigation Overlay

A style of navigation that triggers a full screen overlay. This example utilizes flexbox.

**[Tutorial](https://www.taniarascia.com/full-screen-navigation-overlay/) | [Demo](http://codepen.io/taniarascia/full/yYrXRG/)**

```css
aside {
	position: fixed;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	opacity: 0;
	visibility: hidden;
	z-index: 2;
}
.open {
	opacity: 1;
	visibility: visible;
}
```

```html
<aside>
	<div class="toggle-overlay">
		<a class="close"> Toggle </a>
	</div>
	<nav>
	</nav>
</aside>
```

```js
$('.toggle-overlay').click(function() {
	$('aside').toggleClass('open');
});
```


## Off Canvas Navigation

Slide out navigation that is hidden off canvas until triggered. Inspired by the [Lanyon/Poole theme for Jekyll](http://lanyon.getpoole.com/).

**[Tutorial](https://www.taniarascia.com/off-canvas-navigation/) | [Demo](http://codepen.io/taniarascia/full/QjBwpB/)**

```css
html, body { overflow-x: hidden; }

.position {
	position: absolute;
	top: 0;
	left: 0;
	z-index: 2;
}
@media screen and (min-width: 800px) {
	.position { position: fixed; }
}
aside {
	width: 250px;
	height: 100%;
	position: fixed;
	top: 0;
	left: -250px;
}
main {
	width: 100%;
	position: absolute;
	left: 0;
}
article {
	padding: 0 80px;
}
.show-nav aside, .show-nav .position, .show-nav main { transform: translateX(250px); }
.show-nav .position { position: fixed; }
```

```html
<aside> Navigation </aside>
<a id="nav-toggle" class="position">Toggle</a>
<main>
	<article> Main content </article>
</main>
```

```js
$('#nav-toggle').click(function () {
this.classList.toggle("active");
	if ($('body').hasClass('show-nav')) {
		$('body').removeClass('show-nav');
		} else {
	$('body').addClass('show-nav');
	}
});
```

## Responsive Dropdown Navigation Bar

A classic top navigation bar with dropdowns. The navigation links collapse into a hamburger icon toggle on mobile collapse.

**[Tutorial](https://www.taniarascia.com/responsive-dropdown-navigation-bar/) | [Demo](http://codepen.io/taniarascia/full/dYvvYv/)**

```js
$('nav ul li a:not(:only-child)').click(function (e) {
	$(this).siblings('.nav-dropdown').toggle();
	$('.nav-dropdown').not($(this).siblings()).hide();
	e.stopPropagation();
});
$('html').click(function () {
	$('.nav-dropdown').hide();
});
$('#nav-toggle').click(function () {
	$('nav ul').slideToggle();
});
```

###  Flexbox Grid

A simple, responsive grid made with flexbox. This grid is based on percentages and is infinitely expandable.

**[Tutorial](https://www.taniarascia.com/easiest-flex-grid-ever/) | [Demo](http://codepen.io/taniarascia/full/rOLEGe/)**

```css
.column { flex-basis: 100% }

@media screen and (min-width: 800px) {
	.row {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
	}
		.column { flex: 1; }
		.one-fourth { flex: 2.5; }
		.one-third { flex: 3.3; }
		.half { flex: 5; }
	}
```

```html
<div class="row">
  <div class="column"> 50% </div>
  <div class="column"> 50% </div>
</div>
```

## Float Grid

A simple, responsive grid made with CSS floats and a clearfix hack. This grid is based on percentages rather than the traditional 12-column grid. You can add as many classes as you want columns.

**[Tutorial](https://www.taniarascia.com/you-dont-need-a-framework/) | [Demo](http://codepen.io/taniarascia/pen/GpGdyy)**

```css
.row::before, .row::after {
	display: table;
	content: " ";
	clear: both;
}
.one, .one-third, .two-thirds, .one-fourth, .half { width: 100%; }

@media only screen and (min-width: 800px) {
	.one { width: 100%; }
	.half { width: calc(100% / 2); }
	.one-third { width: calc(100% / 3); }
	.one-fourth { width: calc(100% / 4); }
	.two-thirds { width: calc(100% / 3 * 2); }
	.column { float: left }
}
```
```html
<div class="row">
	<div class="half column"> 50% </div>
	<div class="half column"> 50% </div>
</div>
```





