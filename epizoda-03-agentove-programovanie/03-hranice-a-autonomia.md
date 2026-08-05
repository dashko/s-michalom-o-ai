# Agent potrebuje hranice

Keď agentovi dáme nástroje, nedávame mu len schopnosť odpovedať. Dávame mu schopnosť konať. Preto musíme riešiť aj hranice: čo agent môže čítať, čo môže upravovať, aké príkazy môže spúšťať a kedy sa musí najprv opýtať človeka.

Nie je rovnaké, keď agent prepíše jeden testovací súbor, a keď má prístup k produkčnej databáze, SSH kľúčom alebo príkazom, ktoré vedia mazať dáta.

Dôležité nástroje na riešenie hraníc:

1. approval režimy,
2. sandbox,
3. obmedzené oprávnenia,
4. práca iba v konkrétnom projekte,
5. kontrola rizikových príkazov pred spustením.

Praktické pravidlo: agentovi dávame najmenšie oprávnenia, ktoré potrebuje na aktuálnu úlohu. Nie maximálny prístup pre pohodlie.

Čím väčší prístup agent má, tým väčší je aj blast radius, ak niečo pochopí zle, dostane zlý kontext alebo narazí na prompt injection.

## Blast radius

Blast radius znamená, akú veľkú škodu vie agent spraviť, ak niečo pochopí zle alebo spustí zlý krok.

- Prečítať súbor je malé riziko.
- Prepísať súbor je väčšie riziko.
- Spustiť shell command je ešte väčšie riziko.
- Pustiť deploy alebo zmeniť databázu je úplne iná kategória.

## Úrovne autonómie

Pri agentoch nie je otázka len to, čo vedia spraviť. Dôležitá otázka je aj to, čo im dovolíme spraviť bez potvrdenia.

1. Najbezpečnejší režim je read-only. Agent môže čítať súbory, hľadať v projekte a navrhnúť plán, ale nič nemení.
2. Ďalší stupeň: agent môže navrhovať zmeny, ale každú editáciu alebo shell command musí človek potvrdiť. To je dobrý default pri reálnych projektoch.
3. Ešte voľnejší režim: agent môže automaticky upravovať súbory, ale pri shell príkazoch sa stále pýta.
4. Posledný stupeň je YOLO režim, kde agent robí zmeny a spúšťa príkazy automaticky. Je pohodlný, ale treba ho používať opatrne.

Pravidlo: čím väčší blast radius, tým viac confirmation krokov chceme.

## Odporúčaný postup na začiatok

Na začiatok neodporúčame púšťať agenta rovno v YOLO režime. Lepší postup je:

1. najprv read-only analýza,
2. potom plán,
3. potom malé zmeny s potvrdením,
4. až nakoniec viac autonómny workflow.

Čítať súbor môže agent skoro vždy. Meniť kód väčšinou s kontrolou. Mazať súbory, meniť databázu, deployovať alebo pushovať do remote repozitára by nemal bez jasného súhlasu.
