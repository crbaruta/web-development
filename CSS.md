# FRONTEND DEVELOPMENT

## CSS tips & tricks
* [Bordi](#bordi)

## Oggetti multimediali
* [Video incorporati](#video)


## Bordi
- [Emulare i bordi con il box shadow](https://makandracards.com/makandra/12019-css-emulate-borders-with-inset-box-shadows)
- [Bordi multipli](https://css-tricks.com/snippets/css/multiple-borders/)

Codepen [bordi multipli ottenuti con box-shadow](https://codepen.io/crbaruta/pen/RZgvwa)


## Video incorporati
Generalmente per incorporare un video di youtube si ricorre al tag **tag iframe**. Questa metodo, estremamente semplice presenta due svantaggi
1. il browser deve scaricare una serie di risorse aggiuntive (immagini, CSS e javascript) per il rendering del player di YouTube, anche se il video non viene visionato dall'utente. Questo comporta un aumento del peso complessivo della pagina e del numero di richieste http che il browser deve fare per scaricare le risorse con conseguetne dilatazione dei tempo di caricamento, specialmente se nella pagina sono incorporati più di un video.
2. il codice non è responsive e il palyerdel video non si adattta alle dimensioni dello schermo
Amit Agarwal di Google ha ideato una tecnica efficiente che permette di incorporare il palyer in modo asincrono se l'utente decide di visionare il video e che rende il palyer totalmente responsive ricorrendo a css e javascript
La tecnica consiste nel caricare un immagine fissa di anteprima con sopra l'icona del tasto play in modo da renderla del tutto simile ad un player. Il palyer vero e proprio viene scaricato solo se l'utente clicca sul tasto play posizionato sopra l'anteprima.
Nell'articolo [A Better Method for Embedding YouTube Videos ](https://www.labnol.org/internet/light-youtube-embeds/27941/) è descritta la tecnica di Amit Agarwal

Per rendere repsonsive un video incorporato è necessrio aggiungere un div attorno **tag iframe** e aggiungere degli stili CSS per far si che la dimensione del player si adatti a quella delo schermo.

L'html sarà il seguente
```
<div class="media-container">
	<iframe width="560" height="315" src="https://www.youtube.com/embed/S-aytvTktpk" frameborder="0"></iframe>
</div>
```

Il css sarà il seguente

```
.media-container {
	position: relative;
	padding-bottom: 56.25%;
	height: 0;
	overflow: hidden;
        width:100%;
}

.media-container iframe,  
.media-container object,  
.media-container embed {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
} 
```

Tutto il funzionamento si basa su questa regola: padding-bottom:56.25% 
Andrea Leti ci spiega il concetto nel suo articolo [Video Responsive](https://www.andrealeti.it/video-responsive-o-elestic-video-quando-il-video-deve-adattarsi-soluzione-definitiva/)
In breve il concetto è questo
Il valore del padding 56.25%  è calcolato per video in formato 4:3, in particolare per il formato video di youtube 640×360.
Per video in formato differente è necessario calcolare il padding corretto: ( 100 x altezza del video ) / larghezza.
Ad esempio per un video largo 700px e alto 340px avremo bisogno di un padding di 100 x 340 / 700 = 48,57
Riassumendo
Per i video 4:3 per esempio il classico 640×480 il padding è del 75%
Per i video youtube, vimeo ecc 56.25%
Per i video self-hosted bisogna fare altezza*100 diviso larghezza




