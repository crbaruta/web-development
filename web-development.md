# Web development
List of resources for web development

## General
* [Cos'è il markdown](#cosè-il-markdown) 
* [entità HTML](#entita-html)
* [spunti di riflessione](https://codeburst.io/4-things-you-should-prepare-before-working-as-a-junior-frontend-developer-intern-c8fd6cf382b3)

## CSS
* [CSS Guideslines](#css-gudelines)
* [CSS after and before](#css-after-and-before)
* [RGBa transparent color](https://css-tricks.com/rgba-browser-support/)

## Design

* [Full Screen Navigation Overlay](#full-screen-navigation-overlay) 
* [Off Canvas Navigation](#off-canvas-navigation) 
* [Responsive Dropdown Navigation Bar](#responsive-dropdown-navigation-bar)
* [Responsive, Fluid-Width, Variable-Item Navigation with CSS](https://www.sitepoint.com/responsive-fluid-width-variable-item-navigation-css/)
* [Flexbox Grid](#flexbox-grid)
* [Float Grid](#float-grid)

## Graphics
* [SVG e CSS quando e come usarle](#svg-e-css-quando-e-come-usarle)
* [Tecniche di image rplacement](#tecniche-di-image-replacement)

## Debugging
* [Beginner Guide to Page and Script Debugging with Chrome](https://www.codeproject.com/Articles/273129/Beginner-Guide-to-Page-and-Script-Debugging-with-C)
* [Stepping through JavaScript code in Chrome](http://www.mattzeunert.com/2015/03/29/stepping-through-javascript-code-in-chrome.html)

## Development workflow
* [Git](#git)
* [Gulp Workflow](#gulp-workflow)


## Cos'è il markdown
Il Markdown è un linguaggio di formattazione creato da John Gruber e Aaron Swartz che consente di comporre testi velocemente con una sintassi semplice ed efficace.
Esso permette di inserire titoli, link, elenchi e altri stili utilizzando caratteri regolari e segni di punteggiatura.
I testi possono poi essere convertiti in HTML immediatamente fruibile senza la paura di dimenticare la chiusura di tag o fare errori di scrittura di tag HTML
Il grosso vantaggio del Markdown è quello di generare dei file di testo che contengono la formattazione.
I nostri file diventano così multipiattaforma: possono essere aperti con qualsiasi applicazione e su qualsiasi piattaforma senza perdere le formattazioni applicate al testo.

Per la sintassi fare riferimento a [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) 
[Markdown for GitHub](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
[Markdown supportato da wordpress](https://en.support.wordpress.com/markdown-quick-reference/)

## Entità HTML
* [caratteri speciali](https://css-tricks.com/snippets/html/glyphs/)
* [entià ISO ed HTML](http://labmaster.mi.infn.it/a2/a2396.html)


## CSS Gudelines
High-level advice and [guidelines](https://cssguidelin.es/) for writing sane, manageable, scalable CSS

 

## CSS after and before 
**::after  e ::before** sono pseudo elementi che permettono di inserire un contenuto generato, ovvero non presente nel codice html della pagina. Con **::after** il contentuto viene inserito prima dell'elemento in questione, con **::before** il contenuto viene inserito dopo.
Il contenuto generato è specificato attraverso la proprietà CSS content, che può assumere come valore:
- una stringa di testo: content: "a string"; i caratteri speciali devono essere specificati come entità unicode
- un URL che punti a un’immagine o a un altro documento, es. content: url(/path/to/image.jpg); 
- un contatore numerico: content: counter(li);
- un contenuto vuoto: content: ""; è utile per il clearfix o per inserire immagini come backgound che possono essere ridimensionate col background-size
- il riferimento al valore di un attributo HTML identificato con un selettore di attributo.

La sintassi è la seguente ::afetr (::before), ma IE8 supporta solo :after(:before). Per retrocompatibilità con IE8 usare una sola coppia di due punti

Alcuni riferimenti 
* [::after and ::before](https://css-tricks.com/almanac/selectors/a/after-and-before/)
* [Content](https://css-tricks.com/almanac/properties/c/content/)
* [Gli pseudo elementi](http://www.html.it/pag/14219/gli-pseudo-elementi/)


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

## SVG e CSS quando e come usarle
SVG (Scalable Vector Graphics) è un linguaggio per la descrizione di immagini vettoriali bidimensionali pensato principalmente per il web. Un'immagine vettoriale è descritta mediante un insieme di figure geometriche che definiscono punti, linee, curve e poligoni ai quali possono essere attribuiti colori e anche sfumature. 
In un'immagine vettoriale è possibile ridimensionare a piacere qualsiasi elemento grafico, mantenendone la qualità, l'immagine così può essere riprodotta su supporti di differente natura (stampa, video, plotter, schermo di cellulare ecc.), mantenendo la massima qualità che quei supporti possono fornire.

Ecco alcune guide per utilizzare al meglio le SVG nei nostri progetti web
* [HTML.it: guida all'utilizzo di SVG e CSS](http://www.html.it/guide/svg-e-css-la-guida/)
* [CSS tricks: using SVG](https://css-tricks.com/using-svg/)
* [Coloring SVG in background images](https://codepen.io/noahblon/post/coloring-svgs-in-css-background-images)

Ecco una risorsa per [ottimizzare il codice](https://jakearchibald.github.io/svgomg/) delle nostre SVG online

Immagini SVG responsive
* [Embed SVG into liquid layout or Responsive Web Design](http://soqr.fr/testsvg/embed-svg-liquid-layout-responsive-web-design.php)
* [How to Scale SVG](https://css-tricks.com/scale-svg/)
* [Immagini SVG responsive](http://www.html.it/pag/53868/immagini-svg-responsive-con-le-mediaquery/)



## Tecniche di image rplacement
Le tecniche di image replacement permettono di sostituire il testo di un elemento html con un'immagine di sfondo.
Lo scopo di queste tecniche è quello di poter utilizzare effetti grafici riproducibili solo mediante immagini all'interno di un pagina web, fornendo allo stessto tempo un testo accessibile agli screen reader e ai motori di ricerca.

Al giorno d'oggi il ricorso a queste tecniche non è sempre necessario in quanto abbiamo a disposizione valide alternative quali icon font, webfont, etc per rendere elementi grafici che prima potevano essere resi solo attraverso immagini.

Ecco alcuni riferimenti sulle moderne tecnich edi image replacemnt. 


* [Do We Still Need Image Replacement?](http://www.loganfranken.com/blog/1244/do-we-still-need-image-replacement/)
* [It’s Time to Be Honest about Image Replacement Techniques](https://www.sitepoint.com/its-time-to-be-honest-about-image-replacement-techniques/)
* [Evoluzioni dell'image replacement](http://blog.html.it/24/02/2014/evoluzioni-dellimage-replacement/)
* [Modern Approach To CSS Image Replacement](https://www.appnovation.com/blog/modern-approach-css-image-replacement)

## Git
Git è un sistema di controllo versione distribuito che permette tenere traccia dei cambiamenti che si apportanto al proprio lavoro nel tempo, in modo da poter recuperare una versione specifica di un file o di un intero progetto in qualsiasi momento.

Github è un servizio di hosting per lo sviluppo di progetti software che ricorrono al sistema di controlo di versione Git

### Contribuire ad un progetto presente su Github
1) Creare una copia del progetto sul proprio account Github
Per farlo basta accedere alla pagina del progetto Github a cui si desidera contribuire e cliccare sul bottone **fork**
2) Creare una copia locale del progetto appena forkato
	Per farlo bisogna **clonare** il progetto appena forkato sul proprio PC, col seguente comando
	``` 
	git clone https://github.com/crbaruta/primitive.git
	``` 
	L'indirizzo del progetto da clonare lo recuperiamo dal progetto forkato su Github

	Per verificare i nodi remoti remoti configurati si esegue il comando
	``` 
	$ git remote -v
	``` 
	Il risultato che otteniamo è il seguente
	``` 
	user@DESKTOP-IDVUEQT MINGW64 /c/cb1/primitive_cb (master)
	$ git remote -v
	origin  https://github.com/crbaruta/primitive.git (fetch)
	origin  https://github.com/crbaruta/primitive.git (push)
	```
	L'unico nodo remoto configurato si chiama origin (default se non lo cambio) e corrisponde al progetto appena forkato sul proprio profilo Github

3) Aggiungere un riferimento al repository remoto (detto *remote* da Git) da cui si è *forkato* il progetto, in modo da puntare al progetto originale e catturare evenutuali modifiche introdotte dalla community per poterle trasferire al proprio repository locale.
	Per farlo bisogna recuperare l'indirizzo del progetto originale dalla casella clone URL del progetto originale che abbiamo forkato e utilizzare il comando
	``` 
	git remote add upstream https://github.com/taniarascia/primitive.git
	``` 
	In questo modo avremo due nodi remoti (*remote*)
	* *origin* che corrisponde al fork del progetto sul nostro profilo Github, ed al quale avremo un accesso in lettura/scrittura;
	* *upstream* che corrisponde al progetto principale, e dal quale potremo solo leggere. 

	Verificando la sistuazione col comando usato in precedenza si ottiene
	```user@DESKTOP-IDVUEQT MINGW64 /c/cb1/primitive_cb (master)
	$ git remote -v
	origin  https://github.com/crbaruta/primitive.git (fetch)
	origin  https://github.com/crbaruta/primitive.git (push)
	upstream        https://github.com/taniarascia/primitive.git (fetch)
	upstream        https://github.com/taniarascia/primitive.git (push)
	```

Per caricare il lavoro sul server remoto
```git push origin master``` 
Per [scaricare le modifiche dal server remoto](https://git-scm.com/book/it/v1/Basi-di-Git-Lavorare-coi-server-remote#Scarica-e-condividi-coi-server-remoti)


### Alcuni comandi di Git
* *git status*: mostra lo stato di un repository
* *git clone*: per clonare un progetto da un repository remoto
* *git remote*: mostra i nomi brevi dei nodi remoti configurati 
* *git remote -v*: mostra i nomi brevi e gli URL dei nodi remoti 

Ecco alcune guide a git
* [Git Community Book](https://git-scm.com/book/it/v1)
* [Get Git: guida rapida](http://get-git.readthedocs.io/it/latest/index.html)
	* [Git: disegnare il workflow ideale](http://get-git.readthedocs.io/it/latest/obiettivo_7.html)
* [Github: guida per principianti per contribuire ad un progetto](http://html5today.it/tutorial/github-guida-per-principianti-per-contribuire-ad-un-progetto/)
* [Guida – Git, cos’è e come si usa](http://blog.netsons.com/guida-git-cose-e-come-si-usa/)


* [GitHub Help](https://help.github.com/)
* [A Visual Git Guide](http://marklodato.github.io/visual-git-guide/index-en.html)


## Gulp Workflow
Gulp.js (per gli amici Gulp) è un Task Runner, ovvero uno strumento che consente ottimizzare e automizzare una serie operazioni ricorrenti. In particolare nel caso dello sviluppo di frontend ci troviamo ad eseguire di continuo operazioni ricorrenti (task) quali  
compilare, concatenare e minificare fogli di stile e javascript, ottimizzare immagini etc.
Gulp ci permette di ottimizzare e automatizzare queste operazioni.

* [Primi passi con gulp](http://blog.ingruz.com/primi-passi-con-gulpjs/)
* [Come usare Gulp](http://blog.ingruz.com/primi-passi-con-gulpjs/)
* [usare SaSS con Gulp](https://danieledolci.com/it/blog/posts/usare-sass-con-gulp)
* [npm](https://skillsandmore.org/npm-package-manager-nodejs/)
* [Installare node.js su windows](https://daniloandreini.it/come-installare-node-js-in-windows/) 
* [Npm su windows](https://devnews.it/posts/579774f8eb410c83c50a0566/come_installare_nodejs_su_windows)















