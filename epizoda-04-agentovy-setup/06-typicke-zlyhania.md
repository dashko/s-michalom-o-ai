# Kedy agenta zastaviť a typické zlyhania

## Kedy agenta zastaviť

Agent niekedy začne riešiť viac, než sme chceli. Napríklad:

- mení príliš veľa súborov,
- pridáva dependency,
- robí unrelated refactor,
- opravuje problém iným spôsobom, než bol cieľ,
- alebo sa zasekne v cykle opráv.

Vtedy je lepšie ho zastaviť a zúžiť zadanie. Nie je hanba povedať agentovi: „Stop. Nerob refactor. Oprav iba tento jeden test." Práve toto je praktická kontrola nad agentovým workflow.

## Typické failure modes

Agentické programovanie nie je mágia. Agent vie byť veľmi užitočný, ale má typické zlyhania, ktoré musíme poznať:

- agent začne robiť unrelated refactor,
- opraví test namiesto skutočného bugu,
- pridá novú dependency bez potreby,
- vymyslí si API, ktoré v projekte neexistuje,
- ignoruje existujúci pattern,
- zasekne sa v cykle opravovania,
- alebo tvrdí, že niečo otestoval, aj keď test reálne nespustil.

Preto pri agentovi neveríme len tomu, čo napíše v chate. Pozeráme diff, tool output, testy a build.

## Ako reagovať

Ak agent začne robiť priveľa, najlepšia reakcia nie je nechať ho pokračovať. Najlepšia reakcia je zúžiť zadanie. Napríklad:

```text
Stop. Nerob refactor. Vráť sa k pôvodnej úlohe a oprav iba failing test.
```

Alebo:

```text
Nepoužívaj novú dependency. Skús to spraviť nástrojmi, ktoré projekt už používa.
```

Toto je normálna súčasť práce s agentom. Nie je to chyba workflow, je to riadenie delegovanej práce.
