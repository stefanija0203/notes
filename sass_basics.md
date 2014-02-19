## Sass Basics


### Pre-processing
S obzirom da su CSS fajlovi sve veci, slozeniji i teze za odrzavanje, moze se koristiti preprocesor koji omogucava koriscenje funkcija kao sto su promenljive (variables), umetanje (nesting), miksin (mixin), nasledjivanje (inheritance) i druge koje sluze za lakse pisanje CSS-a.

### Variables
Promenljiva sluzi sa skladistenje informacija koje kasnije zelimo opet da koristimo. Mogu se memorisati boja, font ili bilo koje druge vrednosti. Za varijablu se koristi znak **$**.

### Nested
U HTML-u se selektori mogu umetati jedan u drugi, sto vizuelno predstavlja hijerarhiju. U CSS-u to nije moguce, dok Sass omogucava umetanje selektora koji sledi vizuelnu hijerarhiju HTML-a.

### Partials
Mogu se kreirati parcijalni Sass fajlovi koji sadrze male odlomke CSS-a, koji se mogu dodati u druge CSS fajlove. Sluze za modularizaciju CSS-a i lakse odrzavanje. Naziv ovog fajla pocinje karakterom **_** a poziva se naredbom **@import**.

### Import
Omogucava deljenje Css-a u manje, lakse odrzive delove. Mana je sto se svaki put mora koristiti **@import**, sto stvara novi HTML zahtev.

### Mixins
Omogucavaju pravljenje grupa CSS deklaracijakoje zelimo ponovo da koristimo. Za kreiranje mixina koristi se **@mixin** direktiva i dodaje ime. Moze se koristiti kao CSS deklaracija: **@import ime-mixina**.

### Extend/Inheritance
Jedna od najkorisnijih osobina Sass-a. Koristeci **@extend** omogucava deljenje set CSS osobina iz jednog selektora u drugi.

### Operators
Koriscenje matematickih operatora: **+**, **-**, *****, **/** i **%**.