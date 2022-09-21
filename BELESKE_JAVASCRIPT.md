# BELEŠKE JAVASCRIPT


# CRUD OPERACIJA NA NIZOVIMA
crete nove stavke u nizu
delete nove stave u nizi
update nove stavke u nizi
selektovanje (read) trazene stavke u nizu


## DELETE satvke iz niza pomocu .filter metoda
Ovo je prema principa funkcionalnog programiranaj gde se ulazni podaci ne diraju. Nisat se ne brise iz postojeceg niza nego se pravi novi niz na osnovu starog. A u tom novom jednostavno izostavimo stavku koju smo zeleli da obrisemo.

const noviNiz = niz.filter((item)=>{
  if (item.id === trazeniId) {
    // ako je taj kojeg zelim oda obrisemo
    return false; // false u .filter znaci da nece u sastav novog niza
  }
  // svi ostali ostaju u nizu
  return true; // return true u .filter znaci da ulazi u sastav novog niza
});
// na ovoj liniji koda noviNiz je vec popunjen...


## DELETE stavke iz niza pomocu forEach
let noviNiz = [];
niz.forEach((item)=>{
  if (item.id === trazeniId) {
    // nista ne radimo jer ga ne zelimo u novom nizu
  }
  // sve ostale
  noviNiz.push(item); // guramo ga u novi niz
});
// na ovoj liniji koda noviNiz je vec popunjen...



## Objekti

let id =  2
let kolicina = 15

const stan = {
  id: 1
  kupatilo: '',
  kuhinja: ''
  soba: ''
};

stan.kupatilo
stan.kuhnja
stan.sobe


## for i forEach petlja

  for (let index = 0; index < rec.length; index++) {
    const slovo = rec[index];
    console.log('slovo je:', slovo)
  }

  for (let index = 0; index < 100; index++) {
    console.log('iteracije je:', index)
  }

  let niz = [9,8,7,6,5]
  let index = 0
  for (let item of niz) {
    index++
    console.log(item)
  }

  niz.forEach((item, index)=>{})


## FUNKCIJE
### Arrow funkcije
Moze se pisati na vise nacina
()=>{// neki kod}; // ako nema argumenat onda mora ()
(jedanArgument)=>{//neki kod};
jedanArgument=>{//neki kod}; // ako je smao jedna argument ne mora zagrade
(a,b,c)={// neki kod}; // sa vise argumenat mora zagrada

Skraceni oblici:


state => state.nesto; 
ili
state => (state.nesto)

// ukoliko posle strelice nama viticastih zagrada to je isto kao:

state => {
  return state.nesto;
};

na primer
() => ({
  a: 123,
  b: 234,
  c: 456
});

to je isto kao 
() => {
  return {
    a: 123,
    b: 234,
    c: 456
  };
};


# Koncept kuhinjskih kutija kafa, sol, šećer...

Obicne promenive koje sadrze brojeve ili slova su kao tegle
let caj = 'caj';
let kafa = 'kafa';
let secer = 'secer';

Najjednostavniej vrendosti se zovu PRIMITIVE. primitive su brojeci, 'slova', true false, i onu null.


Slozenije vrednosti su nizovi i objekti.

Objekti su kao tegle koja imaju sovje nalepnice/nazive ali su slepljene i nerazdvojne. Dolaze u paketu.
Svaka od tih pregrada ili slepljenih tegli sa jos naziva IMENOVANI NIZ.

Nizovi ili NEIMENOVANI NIZOVI su kao dugacak lanac tegli kojih ima toliko da ima cak ni ne dajemo imena, nego ih brojcano oznacavmo, kao 0 (prva), 1 (druga), 2, 3, 4, 5 ,6...

PRIMER:
Stan ima nekoliko soba i svakoj mozemo dati konkretan naziv
let stan = {
  kuhinja: '',
  kupatilo: '',
  hodnik: '',
  dnevma: ''
}


Medjutim hotel ima na stotine soba i nemam toliko naziva i nije prakticno da ih tako pamtimo. I onda sobe u hotelima oznacavmo sa brojevima
let hotel = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18] //.. ita kodalje mogu na stotine ili hiljade


Moze i da se kombinuje
na priemr ako hotel ima vise spratova

let hotelVeliki = {
  'sprat1': [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18],
  'sprat2': [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18],
  'sprat3': [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18]
}
// kada trebamo da govorim oo 5-oj sobi na drugom spratu mi u javascriupt kazemo
hotelVeliki.sprat2[4]

Primer trzni centar promenada koji ima dva podsprata za parking na svako mspratu
let promenada: {
  'podrum': {
    a: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18],
    b: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18]
  },
  'sprat1': {
    a: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18],
    b: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18]
  },
  'sprat2': {
    a: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18],
    b: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18]
  }
}
// kad govorimo o trecem parking mestu na b podspratu u podrumu, mi u javascirptu pisemo
promenada.podrum.b[2]





# JAVASCRIPT PISMENOST- Sposbnost pravilnog citanaj koda

Krajnji cilj je da mozem oispravno da procitamo na primer

let nesto = nesto.abc.abc()()().svasta[5]()(2)*drugo().novo()()()[0]()()()


##

let a = 4; // cita se: kreiram opromenjivu a i dodeljujemo vrednost/value 4.
// ljudskim jezikom: kreiram onovu rec a i dajemo joj znacenje 4

let b; // cita se kreiramo pormnjivu b. ali ne dodeljujemo joj vrednost. ostaje undefined

b = 5; // cita se: postojecoj promenjivoj b dodljujemo novu vrednost 5.

b = 7;
// ljudskim jezikom: dali smo drugo znacenje reci b.

## Dot notation i Brackets notation

let srbija = {
  beograd: 'ovo je beograd value',
  'Novi Sad': 'ovo je novi sad value',
  'Niš': 'ovo je Niš value'
}; // cita se kriramo promnjivu srbija i dodeljumo joj vrednost objekat...

srbija.Beograd // dot notation
srbija['Beograd'] // brackets notation
srbija['Novi sad'] // posto ima razmak moze samo brackets notation
srbija['Niš'] // moze sam obracketc notaion zbog slova Š

let niz = ['prvi', 'drugi', 'treci', 'cetvrti', 'peti'];

niz[0] // brackets notacija koja znaci vrednost prve stavke niza
niz[1] // brackets notacija koja znaci vrednost druge stavke niza
niz[4] // brackets notacija koja znaci vrednost pete stavke niza

nekiNiz.length // to znaci vrednost propertija length od niza nekiNiz
nekiNiz.puah() // tn znaci zovemo metod push od niza nekiNiz. konktretno taj metod dodjae jos jednu stavku u niz
nekiNiz[nekiNiz.length - 1] // to znaci vrednost stavke niza koja je za 1 manja od duzine niza. konkretno dodbijamo vrednost poslednje stavke niza

let treciUNizu = niz.indexOf('treci'); // cita se kreramo pormnjivu treciUNizu i dodljujemo mu vrendost koja ce biti jednaka onom sto vrati metod  indexOf (kojeg pozivamo sa argumentom 'treci') niza koj is zove niz. Taj metod vraca index one stavke kod koje je vrednost 'treci'. Znaci vrendost pormenjive treciUNizu ce biti 2 jer je 2 index tj. pozicija gde se nalazi vrednost 'treci' u nizu.

##
// primer da kupatilo ima razlicito znacenje kadna ulici kazes kupatilo i kad u svom satnu pominjes kupatilo.
let kupatilo = 'kupatio uopste';
let bokijevStan = {
  'dnevni boravak0: '',
  kuhinja: '',
  kupatilo: '',
};






















  