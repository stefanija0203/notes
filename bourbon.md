# Bourbon

Obilna biblioteka Sass miksina dizajniranih za jednostavno i lako koriscenje. Cilj miksina je da bude sto priblizniji CSS sintaksi. Burbon koristi SCSS sintaksu.


## Mixins

**Animation** - Podrzava liste vrednosti odvojene zarezom, sto omogucava da se jednom naredbom opise vise osobina.
	

	box:hover {
	  @include animation-name(scale, slide);
	  @include animation-duration(2s);
	  @include animation-timing-function(ease);
	  @include animation-iteration-count(infinite);
	  ________________________________________________________
	  
	  @include animation(scale 1.0s ease-in, slide 2.0s ease);
	}


**Appearance** - Prikazivanje elemanata koriscenjem stilova koji su difoltni za operativni sistem koji se koristi.


	@include appearance(none);


**Backface-visibility** - Odredjuje hoce li se prikazati nalicje elementa kada je okrenut korisniku. Nalicje elemanta je uvek transparentna pozadina koja, kada je vidljiva, prikazuje svoj odraz.


	@include backface-visibility(visible);


**Background** - Dodavanje vise pozadina. Moze imati 1 i vise argumenata.


	@include background(linear-gradient(red, green) left repeat);
	@include background(linear-gradient(red, green) left repeat, radial-gradient(red, orange) left repeat);
	@include background(url("/images/a.png"), linear-gradient(red, green), center no-repeat orange scroll);


**Background-image** - Za ulancavanje slika pozadine i/ili linear/radial-gradient u jednoj background-image naredbi. Podrzava do 10 slika.


	// Linear-gradient
	@include background-image(url("/images/a.png"), linear-gradient(white 0, yellow 50%, transparent 50%));

	// Multiple linear-gradients
	@include background-image(linear-gradient(hsla(0, 100%, 100%, 0.25) 0%, hsla(0, 100%, 100%, 0.08) 50%, transparent 50%), linear-gradient(#4e7ba3, darken(#4e7ba4, 10%)));


Sve CSS background osobine podrzavaju odvajanje vrednosti zarezom , tako da se za vise slika mogu podesiti osobine kao sto su pozicija, ponavljanje i td.


	@include background-image(url("/images/a.png"), url("images/b.png"));
	background-position: center top, center;
	background-repeat: no-repeat, repeat-x;


**Background-size** - Dimenzije slika su razdvojene zarezom.


	@include background-size(50% 100%); // Single
	@include background-size(50% 100%, 75% 100%); // Multiple


**Border-image**


	@include border-image(url(/images/border.png) 27 repeat);


**Border-radius** - Za ciljanje ivica koje zelimo da zaoblimo.


	@include border-top-radius(5px);
	@include border-bottom-radius(5px);
	@include border-left-radius(5px);
	@include border-right-radius(5px);


**Box-shadow** - Za postavljanje senke iza boxa. Podrzava pojedinacne ili visestruke elemente.


	@include box-shadow(0 0 5px 3px hsla(0, 0%, 0%, 0.65));



**Box-sizing** - Menja box-model elementa koji se primenjuje.


	@include box-sizing(border-box);



**Columns** - Sve aktuelne CSS osobine kolona su pordzane.


	@include columns(12 8em);
	@include column-rule(1px solid green);


**Flex-box** - Fleksibilni elementi se mogu siriti i supljati u zavisnosti od slobodnog prostora box-a u kom se nalaze. Element je fleksibilan kada je definisana box-flex osobina. Ona sadrzi vrednost koja predstavlja fleksibilnost elementa. (0-nefleksibilan element; sto je veca vrednost to je element fleksibilniji)


	div.parent {
		@include display-box;
		@include box-align(start);
		@include box-orient(horizontal);
		@include box-pack(start);
	}

	div.parent > div.child {
	    @include box-flex(2);
	}

	// Alternative custom shorthand mixin.
	div.parent {
	    @include box($orient: horizontal, $pack: center, $align: stretch); // defaults
	    @include box(vertical, start, stretch);
	}
	

**Font-face** - Omogucava lakse koriscenje fontova.


	@include font-face(SourceSansPro, '/fonts/Source_Sans_Pro/SourceSansPro-Regular');
	@include font-face(SourceSansPro, '/fonts/Source_Sans_Pro/SourceSansPro-Bold', bold);
	@include font-face(SourceSansPro, '/fonts/Source_Sans_Pro/SourceSansPro-Italic', normal, italic);


**HIDPI-media-query** - Dozvoljava generisanje medija upita koji se odnosena HIDPI uredjaje. Prihvata opcionalni ratio argument(default ratio 1.3). HIDPI - uredjaji koji imaju veliki broj pixela na malom ekranu.


	@include hidpi(1.5) {
  	    width: 260px;
	}


CSS Output


	@media only screen and (-webkit-min-device-pixel-ratio: 1.5),
	only screen and (min--moz-device-pixel-ratio: 1.5),
	only screen and (-o-min-device-pixel-ratio: 1.5/1),
	only screen and (min-resolution: 144dpi),
	only screen and (min-resolution: 1.5dppx) {
	  width: 260px;
	}


**Image-rendering** - daje predlog korisniku kako da koristi svoju sliku.


	@include image-rendering(optimizeSpeed);


**Keyframes** - Za generisanje vendor prefiksa.


	@include keyframes(fadeIn) {
	    from {
	    @include transform(scale(0));
	    }
	    to {
	    @include transform(scale(1));
	    }
	}


CSS Output


	@-webkit-keyframes fadeIn {
		from {
    		-webkit-transform: scale(0);
    	}
		to {
			-webkit-transform: scale(1);
		}
	}

	@-moz-keyframes fadeIn {
		from {
			-moz-transform: scale(0);
		}
		to {
			-moz-transform: scale(1);
		}
	}

	@-o-keyframes fadeIn {
		from {
    		-o-transform: scale(0);
    	}
		to {
	    	-o-transform: scale(1);
	    }
	}

	@keyframes fadeIn {
		from {
    		transform: scale(0);
    	}
		to {
    		transform: scale(1);
    	}
    }


**Linear-gradient** - Gradijent pozicija je opcionalna. Moze biti izrazena u stepenima. Podrzava do 10 boja.


	@include linear-gradient(#1e5799, #2989d8);
	@include linear-gradient(to top, #8fdce5, #3dc3d1);
	@include linear-gradient(to top, #8fdce5, #3dc3d1, $fallback: red);
	@include linear-gradient(50deg, #1e5799 0%, #2989d8 50%, #207cca 51%, #7db9e8 100%);


**Perspective** - Odredjuje razdaljinu izmedju ravni z=0 i korisnika kako bi 3d pozicioniranom elementu dao neku perspektivu.


	@include perspective(300px);
	@include perspective-origin(30% 30%);


**Placeholder** - Mora biti umetnut, ugnezden.


	input {
	    width: 300px;

	    @include placeholder {
	    color: red;
	    }
	}


CSS output


	input {
	    width: 300px;
	}

	input::-webkit-input-placeholder {
	    color: red;
	}
	input:-moz-placeholder {
	    color: red;
	}
	input::-moz-placeholder {
	    color: red;
	}
	input:-ms-input-placeholder {
	    color: red;
	}


**Radial-gradient** - Gradijent pozicija je opcionalna. Moze biti izrazena u stepenima. Podrzava do 10 boja.


	@include radial-gradient(#1e5799, #3dc3d1);
	@include radial-gradient(#1e5799, #3dc3d1, $fallback: red);
	@include radial-gradient(circle at 50% 50%, #eee 10%, #1e5799 30%, #efefef);


**Transform** - Promena pozicije i izgleda elementa u 3D koordinatnom sistemu. Vrednosti: translate(menja poziciju), rotate(rotira se oko svoje ose ili oko x/y/z ose), scaled(menja velicinu za odredjeni odnos) i skewed(menja samo jednu dimenziju elementa, tj. razvlaci ga po x, y ili z osi).  
transform-origin - menja poziciju elementa;  
transform-style - menja stil elementa.


	@include transform(translateY(50px));
	@include transform-origin(center top);
	@include transform-style(preserve-3d);


**Transition** - Podrzava vise tranzicija.


	@include transition (all 2.0s ease-in-out);
	@include transition (opacity 1.0s ease-in 0s, width 2.0s ease-in 2s);


Za tranziciju su definisane vendor-prefix osobine, tako da je bolje njih koristiti nego miksine.


	@include transition-property (transform);
	@include transition-duration(1.0s);
	@include transition-timing-function(ease-in);
	@include transition-delay(0.5s);


**User-select** - Kontrolise pojavu selekcije, ali nema nikakav efekat na operacije selekcije.


	@include user-select(none);




## Functions


**Compact** - Uklanja vrednosti iz liste koje imaji vrednost false.


	$full:  compact($name-1, $name-2, $name-3, $name-4, $name-5, $name-6, $name-7, $name-8, $name-9, $name-10);


**Flex-grid** - Varijable $fg-column, $fg-gutter i $fg-max-columns moraju biti definisane u baznom CSS fajlu da bi pravilno koristila flex-grid funkcija.


	$fg-column: 60px;             // Column Width
	$fg-gutter: 25px;             // Gutter Width
	$fg-max-columns: 12;          // Total Columns For Main Container

	div {
	    width: flex-grid(4);        // returns (315px / 1020px) = 30.882353%;
	    margin-left: flex-gutter(); // returns (25px / 1020px) = 2.45098%;

	    p {
	        width: flex-grid(2, 4);   // returns (145px / 315px) = 46.031746%;
	        float: left;
	        margin: flex-gutter(4);   // returns (25px / 315px) = 7.936508%;
	    }

	    blockquote {
	    	float: left;
	    	width: flex-grid(2, 4);   // returns (145px / 315px) = 46.031746%;
	  }
	}


**Golden-ratio** - Vraca odnos zadatog broja(default ratio 1.618). Za prvi argument se mora odrediti pixel ili em vrednost. Drugi argument je ceo broj za povecanje vrednosti.  
Moze biti umotana u Sass funkcije abs(), floor() i ceil() da bi dobila apsolutnu vrednost ili je zaokruzila.


	// Pozitivan broj ce povecavati zlatni odnos
	font-size: golden-ratio(14px,  1);		// returns: 22.652px


	// Negativan broj ce smanjivati zlatni odnos
	font-size: golden-ratio(14px, -1);		// returns: 8.653px
	

**Grid-width** - Podesava i prati dizajn resetki. Varijable $gw-column i $gw-gutter moraju biti definisane u baznom CSS fajlu da bi se pravilno koristila grid-width funkcija.


	$gw-column: 100px;          // Column Width
	$gw-gutter: 40px;           // Gutter Width

	div {
	    width: grid-width(4);     // returns 520px;
	    margin-left: $gw-gutter;  // returns 40px;
	}


**Linear-gradient** - Koristi se sa background-image kao funkcija, ima iste argumente kao linear-gradient miksin, s tim sto se direktiva @include ne odnosi na linear-gradient vec na background-image.


	@include background-image(linear-gradient(white 0, yellow 50%, transparent 50%));


**Modular-scale** - Vraca modularnu skalu zadatog broja. Za prvi argument se odredjuje pixel ili em vrednost. Drugi argument je ceo broj za povecanje vrednosti. Treca vrednost je ratio broj.  
Moze biti umotana u Sass funkcije abs(), floor() i ceil() da bi dobila apsolutnu vrednost ili je zaokruzila.


	div {
	    // Pozitivan broj ce povecavati vrednost
	    font-size:        modular-scale(14px,   1, 1.618); // returns: 22.652px

	    // Negativan broj ce smanjivati vrednost
	    font-size:        modular-scale(14px,  -1, 1.618); // returns: 8.653px

	    // floor(zaokruzuje vrednost na manji broj) i ceil(zaokruzuje vrednost na veci broj)
	    font-size: floor( modular-scale(14px, 1, 1.618) ); // returns: 22px
	    font-size:  ceil( modular-scale(14px, 1, 1.618) ); // returns: 23px
	}


**Radial-gradient** - Koristi se sa background-image kao funkcija, ima iste argumente kao radial-gradient miksin, s tim sto se direktiva @include ne odnosi na radial-gradient vec na background-image.


	@include background-image( radial-gradient(#1e5799, #3dc3d1) );
	@include background-image( radial-gradient(50% 50%, circle cover, #1e5799, #3dc3d1) );
	@include background-image( radial-gradient(50% 50%, circle cover, #eee 10%, #1e5799 30%, #efefef) );


**Tint&Shade** - Tint:miks odredjene boje i bele; shade: miks odredjene boje i crne.


	background: tint(red, 40%);
	background: shade(blue, 60%);



## Add-ons

**Button** - Podrzava parametar za stil i, opcionalno, argument za boju. Stilovi dugmeta su simple(default), pill i shiny.  

Simple Button Style - pozvan bez argumenata vraca dugme plave boje.


	button {
	  	@include button;
	}


Pill Button Style 


	button {
	    @include button(pill);
	}


Shiny Button Style - Mogu se definisati boja, gradijent, ivica, senke box-a i teksta i boja teksta na dugmetu. Miksin podesava svetli tekst kada je pozadina tamna i tamni tekst kada je pozadina svetla.


	button {
	    @include button(shiny, #ff0000);
	}


**Clearfix** - Vraca clearfix na selektor gde je miksin definisan.


	div {
	    @include clearfix;
	}


**Font-family** - Definisanje fontova kao varijable zbog odredjenih pogodnosti.


	font-family: $helvetica;
	font-family: $georgia;
	font-family: $lucida-grande;
	font-family: $monospace;
	font-family: $verdana;


CSS Output


	font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
	font-family: Georgia, Cambria, "Times New Roman", Times, serif;
	font-family: "Lucida Grande", Tahoma, Verdana, Arial, sans-serif;
	font-family: "Bitstream Vera Sans Mono", Consolas, Courier, monospace;
	font-family: Verdana, Geneva, sans-serif;


**Hide-text** - slika koja zamenjuje miksin.


	div {
	    @include hide-text;
	    background-image: url(logo.png);
	}


**HTML5 Input Type** - Pruza 3 varijable od kojih svaka sadrzi listu svih HTML5 tekstualnih ulaza, iskljucujuci textarea. Uz varijablu se koristi interpolacija.


	#{$all-text-inputs} {
	    border: 1px solid green;
	}

	#{$all-text-inputs-hover} { // Target the :hover pseudo-class
	    background: yellow;
	}

	#{$all-text-inputs-focus} { // Target the :focus pseudo-class
	    background: white;
	}


CSS Output


	input[type="email"], input[type="number"],   input[type="password"], input[type="search"],
	input[type="tel"],   input[type="text"],     input[type="url"],      input[type="color"],
	input[type="date"],  input[type="datetime"], input[type="datetime-local"],
	input[type="month"], input[type="time"],     input[type="week"] {
	  border: 1px solid green;
	}

	input[type="email"]:hover, input[type="number"]:hover,   input[type="password"]:hover, input[type="search"]:hover,
	input[type="tel"]:hover,   input[type="text"]:hover,     input[type="url"]:hover,      input[type="color"]:hover,
	input[type="date"]:hover,  input[type="datetime"]:hover, input[type="datetime-local"]:hover,
	input[type="month"]:hover, input[type="time"]:hover,     input[type="week"]:hover {
	  background: yellow;
	}

	input[type="email"]:focus, input[type="number"]:focus,   input[type="password"]:focus, input[type="search"]:focus,
	input[type="tel"]:focus,   input[type="text"]:focus,     input[type="url"]:focus,      input[type="color"]:focus,
	input[type="date"]:focus,  input[type="datetime"]:focus, input[type="datetime-local"]:focus,
	input[type="month"]:focus, input[type="time"]:focus,     input[type="week"]:focus {
	  background: white;
	}


**Pixel to ems** - Input se racuna na osnovu roditeljske vrednosti, cija je difoltna vrednost 16px, a ona se moze promeniti dodavanjem druge vrednosti.


	font-size: em(12);
	font-size: em(12, 24);


CSS Output


	font-size: 0.75em;
	font-size: 0.5em;


**Position** - Prvi argument je opcionalan, i ima difoltnu vrednost relative. Drugi argument je razmakom razdvojena lista.


	position: relative;
	top: 0px;
	left: 100px;


CSS Output


	@include position(relative, 0px 0 0 100px);


**Prefixer Settings** - Po difoltu, Burbon vraca sve vendor-prefikse sa svaki miksin, i prefiksi kao varijable imaju vrednost true. Ovo se moze promeniti podesavanjem bilo koje varijable na vrednost false na pocetku dokumenta.


	$prefix-for-webkit:    true;
	$prefix-for-mozilla:   true;
	$prefix-for-microsoft: true;
	$prefix-for-opera:     true;
	$prefix-for-spec:      true;\


**Prefixer** - Za generisanje odredjenih vendor-prefiksa. Prefiksi: webkit, moz, ms, o, spec.


	@mixin box-sizing($box) {
	    @include prefixer(box-sizing, $box, webkit moz spec);
	}


CSS Output


	-webkit-box-sizing: $box;
  	   -moz-box-sizing: $box;
      	    box-sizing: $box;


**Retina-image** - Retina slike imaju 2 puta vise piksela nego sto uredjaj pozdrzava. Miksin koristi _2x.png kao difoltni retina naziv fajla.


	span {
	    @include retina-image(home-icon, 32px 20px)
	}


CSS Output


	span {
	     background-image: url(home-icon.png); 
	}
	@media only screen and (-webkit-min-device-pixel-ratio: 1.3),
	only screen and (min--moz-device-pixel-ratio: 1.3),
	only screen and (-o-min-device-pixel-ratio: 1.3 / 1),
	only screen and (min-resolution: 125dpi),
	only screen and (min-resolution: 1.3dppx) {
	    span {
		    background-image: url(home-icon_2x.png);
		    background-size: 32px 20px; }
	}


**Size** - Definisanje visine i sirine. Po difoltu, vrednost izrazena u pikselima.


	@include size(25);        // width: 25px; height: 25px;
	@include size(30px 70px); // width: 30px; height: 70px;
	@include size(auto 80px); // width: auto; height: 80px;


**Timing-functions** - varijable koje se mogu koristiti sa CSS animacijama i tranzicijama.


	@include transition(all 5s $ease-in-circ);


**Triangle** - Argumenti: $size, $color i $direction.


	@include triangle(12px, gray, down);


Directions: up, down, left, right, up-right, up-left, down-right i down-left.
