# Sass - Syntactically Awesome Stylesheets


Ekstenzija CSS-a, koja dodaje snagu i eleganciju na osnovni jezik. Omogucava koriscenje: variables, nested, mixins, import inline. Sluzi za dobru organizaciju CSS fajlova, dobijanje malih i njihovo lako i brzo koriscenje.

### Karakteristike:
* CSS3 kompatibilan;
* Ekstenzije kao sto su variable, nested i mixins;
* Vise korisnih funkcija za manipulisanje bojama i drugim vrednostima;
* Napredne karakteristike kao sto su control directives;
* Formatiran, prilagodljiv izlaz;
* Firebug integration.


## Syntax
1. SCSS (Sassy CSS) je prosirenje sintakse CSS3. Svaki vazeci CSS fajl je validan SCSS fajl sa istim znacenjem. Fajlovi koji koriste ovu sintaksu imaju .scss ekstenziju.
2. Starija sintaksa, **indented syntax** (ili samo Sass), obezbedjuje jasniiji, sazetiji nacin pisanja CSS-a. Radije koristi uvlacenje nego zagrade za umetanje od selektora, i nove redove nego tacku i zarez za odvajanje osobina.

Svaka sintaksa moze da ubaci fajlove pisane u drugoj. Fajlovi se mogu konvertovati iz jedne sintakse u drugu:

SASS -> SCSS: $ sass-convert style.sass style.scss

SCSS -> SASS: $ sass-convert style.scss style.sass

## Encodings
Sass pretpostavlja da se svi CSS fajlovi kodiraju koristeci kodni sistem svog operativnog sistema. Kod vecine je to **UTF-8** koji je standard za Web, ali to moze biti i lokalno okruzenje. Ukoliko zelimo da koristimo drugacije kodiranje, koristimo **@charset ime-koda** deklaraciju, koja se stavlja na samom pocetku fajla. Kod koji se koristi mora biti konvertibilan Unicode-u.

Sass ce izlazne fajlove kodirati koriscenjem koda ulaznog fajla, tako da ulazni fajl mora ima **charset** deklaraciju, inace ce se koristiti **UTF-8**. Ako je neki fajl sa **@charset** deklaracijom uvezen (@import) Sass ce ga kodirati kodom glavnog fajla.

## CSS Extensions
**Nested rules** - Sass dozvoljana Css naredbama da budu umetnute jedna u drugu. Umetnuta naredba vazi samo za spoljasnji selektor. Ovim se izbegava ponavljanje roditeljskih selektora, i slozene CSS rasporede cini mnogo jednostavnijim.

**Referencing Parent Selectors** - Ukoliko zelimo da imamo specijalni stil za selektor kada je prekriven (hovered) ili kada element ima odredjenu klasu, moze se odrediti gde ce roditeljski selektor biti ubacen koristeci **&** karakter. U CSS-u karakter **&** ce biti zamenjen roditeljskim selektorom.

**Nested properties** - U CSS-u postoji nekoliko osobina koje su "namespaced", npr. font-family, font-size i font-weight, i ovde je font "namespace". U tom slucaju slucaju, pise se samo "namespace" i onda se umecu podosobine. "Namespace" takodje moze da ima vrednost.

**Placeholder Selector** - Oznacava se sa **%** i koristi uz **@extend**.

## Comments
Viselinijski komentari se okruzuju sa **/* ** i ** */**, a jednolinijski pocinju sa **//**. Viselinijski komentari se prikazuju u CSS-u, dok jednolinijski ne. Ukoliko je prvi karakter komentara **!**, komentar ce biti prikazan bez obzira na to koliko redova sadrzi.

## Sass Script
Podrzava mali skup ekstenzija pod nazivom SassScript koji omogucava koriscenje svojstava promenljivih, aritmeticke i dodatne funkcije, kao i one za generisanje selektora i imena osobina, sto je korisno za pisanje miksina (mixins). Za generisanje se koristi interpolacija **#{}**.

### Interactive shell
SassScript se moze pisati i koriscenjem terminala. Za pokretanje se koristi naredba **sass -i**.

### Variables: $
Varijabla je dostupna samo u nivou umetnutog selektora u kom je definisana. Ukoliko je definisana izvan selektora, onda je dostupna svuda.

### Data types
* Brojevi (npr, 1.2; 13; 10px);
* String, sa i bez navodnika (npr. "foo"; 'bar'; baz);
* Boje (npr. blue; #04a3f9; rgba(225,0,0,0.5));
* Boolean (true; false);
* Nula (null);
* Lista vrednosti, odvojena razmakom ili zarezom (npr. 1.5em 1em 0 2em, Helvetica, Arial, sans-serif).

**Strings** - Stringovi mogu biti sa navodnicima (" "; ' ') i bez. Kada se koristi interpolacija **#{}** navodnici se ne prikazuju.

**Lists** - Lista je niz vrednosti odvojenih razmakom ili zarezom. I individualne vrednosti se mogu predstavljati kao liste. 

Sass funkcije: **nth function** pristupa stavkama u listi: **join function** zdruzuje vise listi; **append function** dodaje stavke listi. Naredba **@each** dodaje stil za svaku stavku posebno. 

Lista moze da sadrzi listu. Ukoliko unutrasnja lista ima iste separatore kao spoljasnja, koriste se zagrade da se oznaci gde pocinje unutrasnja lista i gde se zavrsava. Lista moze biti prazna, oznacava se sa **()**.

### Operations
Numericke operacije: addition **+**, substraction **-**, multiplication *****, division **/** i modulo **%**.
Relacioni operatori **<**, **>**, **<=**, **>=** za brojeve; znakovi jednakosti **==**, **!=** za sve tipove.

Karakter **/** ce se koristiti kao znak deljenje ako se vrednost, ili bilo koji njen deo cuva kao promenljiva: ako je vrednost okruzena zagradama; ako se vrednost koristi kao deo drugog matematickog izrazavanja.

Ukoliko zelimo da prikazemo promenljive zajedno sa karakterom **/** koristimo interpolaciju **#{}** da ih ubacimo.

**Boolean operations** - and, or i not.

### Interpolation
Mogu se koristiti varijable u selektorima, osobine i njihove vrednosti koristeci **#{}**.

## @-Rules and Directives

### @import
Sluzi za uvoz SCSS i Sass fajlova, koji se spajaju u jedan CSS fajl. Moguce je uvesti vise fajlova odjednom.

Parcijalni Sass fajlovi predstavljaju male odlomke CSS-a sa odredjenim stilom. U istom direktorijumu ne mogu postojati parcijalni i 'neparcijalni' fajlovi sa istim imenom, npr. _colos.scss i colors.scss.

### @media
Moze biti umetnuta u CSS naredbe. Ukoliko nije, bice na pocetku CSS fajla, smestajuci sve selektore na putu unutar komande.
**@media** upiti se mogu umetati jedan u drugi. Mogu da sadrze SassScript izraze (varijable, funkcije i operatore) na mestu imena, kao i vrednosti osobina.

### @extend
Koristi se kada jedna klasa treba da preuzme stil druge klase. Umesto klase moze biti i neki selektor koji sadrzi samo jedan element. Selektor se moze produziti za vise od jednog selektora, sto znaci da nasledjuje osobine svih pridruzenih selektora. Selektoru je moguce pridruziti selektor kome je vec pridruzen neki treci selektor.

Selektor sekvenca moze pridruziti selektor koji se pojavljuje u drugoj sekvenci, i tada se te dve sekvence moraju spojiti.

Imamo stilove za klase koje samo pridruzujemo, ne koristimo ih u HTML-u. Za to koristimo 'placeholder selector', koji se moze pridruziti ali ne i generisati kao ostali selektori.

Ukoliko se **@extend** koristi u **@media** (ili drugoj CSS direktivi), moze da pridruzuje samo selektore koji se nalaze u tom bloku.

##Control Directives

**@if** - Uzima SassScript izraz i koristi stilove umetnute ispod njega ako izraz vraca bilo sta osim **false** i **null**. **@if** izraz moze biti pracen sa vise **@ else if** i jednim **@else** izrazom.

**@for** - Petlja koja se nekoliko puta ponavlja, i svakom izlazu se pridruzuje odredjeni stil.

**@each** - Ova naredba ima formu **@each $var in < list >**. **$var** moze biti bilo koja promenljiva, npr. **$lenght** ili **$name**. Svakoj promenljivoj se dodedjuje odredjeni stil.

**@while** - Sve dok se ispunjava dati uslov, tj. dok ne dodje do vrednosti **false**, izlaz ce imati odredjeni stil.

## Mixin Directives

Mixins dozvoljavaju definisanje stilova koji se mogu vise puta koristiti kroz dokument. Mogu da sadrze CSS naredbe i sve sto je dozvoljeno u Sass dokumentima.

Definisanje: **@mixin ime-mixina (argument opcionalno) {blok sa sadrzajem mixina}**

Mogu sadrzati selektore (koji mogu imati roditeljske reference) i njihove osobine. Ukljucuju se u dokument uz **@include** direktivu. Mixini se mogu ukljuciti u dokument i van neke naredbe, sve dok direktno ne definisu neku osobinu ili koriste roditeljsku referencu. Mogu ukljuciti i druge mixine, ali ne i sebe. 

Argumenti mixina se pisu kao imena promenljivih razdvojena zarezima, u zagradama posle imena. Mixini mogu da odrede difoltne vrednosti za svoje argumente.

Sass podrzava "variable arguments" - varijabilan broj argumenata koji se prosledjuje kao lista. Naziv argimenta je pracen sa **...**.
