# BELEŠKE ZA REAT HOOKS

## Primeri odkale dolazi logika
Kada na primer imamo tri stranice koji imaju vizuelno identican header (vrh stranice)
mi u svaku starnicu stavljaju jednu istu komponentu <Header/> kako bi vrh svakestarne isto izgledao a da ne moramo tri puta da ga pisemo.


## Ista logika za vrh funckija u javascriptu

ako na primer imamo tri funckije koje imaju istu stvar na vrhu

const izracunajObimKruga = (precnik)=> {
  const pi = 3.14;

  // neke komande za racunanje povrsine kruga
  // ...
};

const izracunajPovrsinuKruga = (precnik)=> {
  const pi = 3.14;

  // neke komande za racunanje povrsine kruga
  // ...
};


const izracunajPovrsinuKrugaOdPoluprecnika = (poluprecnik)=> {
  const pi = 3.14;

  // neke komande za racunanje povrsine kruga
  // ...
};


sve tir funkcije na vrhu imaju const pi = 3.14;
znaci prva linija u svim funkcijama je identicna

Bitno je da u dnjim linijama koda kada zatreba promenjiva pi da ona postoji, nije bitno na kojoj liniji je deklarisana i kako je nastala, mogla je biti i globalna a mogla je bi i importovana iz nekog fajla.
Bitno je samo da nakon tog vrha funcikcija postoji pormnjiva pi i da ona ima valu 3.14 i sve ostale komande ispod ce isto da rade

### sad pravimo zajednicki vrh za sve tri funkcije

const vrhFunkcije = ()=> {
  const pi = 3.14;
  const korenIzDva = 1.41;
  return {
    pi: pi,
    korenIzDva: korenIzDva
  }
};

const izracunajObimKruga = (precnik)=> {
  const {
    pi
  } = vrhFunkcije();

  // neke komande za racunanje povrsine kruga
  // ...
};

const izracunajPovrsinuKruga = (precnik)=> {
  const {
    pi
  } = vrhFunkcije();

  // neke komande za racunanje povrsine kruga
  // ...
};


const izracunajPovrsinuKrugaOdPoluprecnika = (poluprecnik)=> {
  const {
    pi
  } = vrhFunkcije();

  // neke komande za racunanje povrsine kruga
  // ...
};


## React custom hoooks

Ako u tri react komponente imamo state sledeci pocetak

const NekaKomponenta = ()=> {
  const [users, setUsers] = useState();
  // nakon ove linije koda postoji state koji se zove users u dve promenjive users i setUsers.
}

mi onda napravimo zajednicki vrh funkcije koji zovemo react CUSTOM HOOK koji izgleda ovako

// ovo napravmo u fajlu use-user-state.js
export const = useUserState = () => {
  const [users, setUsers] = useState();
  return {
    users, 
    setUsers
  }
};

i onda na vrhu svake komponente


const NekaKomponenta = ()=> {
  const {users, setusers} = useUserState();
  // nakon ove linije koda postoji state koji se zove users u dve promenjive users i setUsers.

}

const DrugaKomponenta = ()=> {
  const {users, setusers} = useUserState();
  // nakon ove linije koda postoji state koji se zove users u dve promenjive users i setUsers.

}

const trecaKomponenta = ()=> {
  const {users, setusers} = useUserState();
  // nakon ove linije koda postoji state koji se zove users u dve promenjive users i setUsers.

}





