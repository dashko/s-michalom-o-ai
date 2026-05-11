# Zamotaný prompt

Toto je príklad opačného extrému: prompt obsahuje priveľa tém, podmienok, otázok a vedľajších problémov naraz.

```text
Napíš správu predajcovi iPhone-u po slovensky, chcem detaily a či pôjde na moju TV.
Nie som si istý, aký je stav baterky a či je prasknutý displej.
Problém je, že mojej mamke ide len niekedy zdieľanie obrazovky telefónu na televízor, a ja nechcem, aby to bolo „len niekedy“, lebo to potom závisí od toho, či sa práve trafí správna Wi-Fi.
Ak je správna Wi-Fi, tak neviem, či je TV polovico-uspalá – lebo to potom tiež nejde.
Ak nie je uspaná, tak asi by si mohol napísať, ako ju zobudiť.
Potom sa telefon môže prepnúť na dáta, aj keď nie je uspaná TV, a potom sa tvári, že sa telefon a TV nepoznajú.
Internet tiež je problém – niekedy ide, niekedy nie, aj keď ide TV, alebo je telefón zamrznutý.
Mám kúpiť Google Telefón alebo iPhone? Niekedy ide ten, niekedy ten druhý.
Pri tomto telefone by fungovalo zdielanie obrazovky? Asi by som nemal kúpiť telefón, ale čo mám robiť – telefón potrebujem.
Je problém v Netflixe alebo YouTube? Myslíš, že je problém vo Wi-Fi? Kamošovi ide Netflix pomaly, čo je ďalšia záhada – lenže často je to sieťová špička, prehustené Wi-Fi alebo to, že zrkadlenie tlačí všetko cez telefón a dusí sa to.
Kamoš uviedol Google Cast, ja radšej AirPlay, ale aj AirPlay je „lepší“ len vtedy, keď ho TV fakt poriadne podporuje – nie akože. Dalo by sa to aj káblom AirPlay, lebo je stabilnejší, takže to môže byť len zlomený kábel alebo port. Dáva to zmysel?
A moja TV TCL 55P635 (vlastný OS) musí ísť normálne, nie ako u mamy, kde je to AirPlay lotéria.
```

## Prečo je problémový

V jednom prompte je zmiešaných viac samostatných úloh:

- napísať správu predajcovi,
- zistiť stav batérie,
- zistiť stav displeja,
- riešiť zrkadlenie obrazovky,
- diagnostikovať Wi‑Fi,
- porovnávať iPhone a Android telefón,
- riešiť Netflix, YouTube, AirPlay, Google Cast a kábel.

Model môže odpovedať dlho, ale nemusí splniť hlavný cieľ. Často preskočí niektoré podmienky, zmení priority alebo začne riešiť vedľajšie témy.

## Lepší postup

Rozdeľte úlohu na menšie kroky, napríklad:

1. Najprv napísať správu predajcovi.
2. Samostatne zistiť, aké otázky treba položiť k stavu telefónu.
3. Samostatne riešiť kompatibilitu zrkadlenia s TV TCL 55P635.
4. Samostatne diagnostikovať problém so sieťou alebo streamovaním.
