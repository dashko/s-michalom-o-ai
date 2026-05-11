# Univerzálna šablóna promptu

Dobrý prompt je často lepšie písať ako krátku špecifikáciu, nie ako spontánnu otázku.

Táto šablóna nie je jediný správny formát, ale je to dobrý základ.

## Šablóna

```text
System / Instructions:

- ROLA: Si {rola}.
- CIEĽ: Tvojou úlohou je {konkrétny výsledok}.
- KROKY:
  1. {krok 1}
  2. {krok 2}
  3. {krok 3}
- OBMEDZENIA:
  - Publikum: {publikum}
  - Tón: {tón}
  - Dĺžka: {dĺžka}
  - Nerob: {čo nerobiť}
- FORMÁT:
  - {email / zoznam / tabuľka / JSON / iný formát}

User message:

- VSTUPY:
  - {text, dáta, dokument, linky alebo zadanie}
```

## Čo jednotlivé časti znamenajú

- **Rola** – z akej perspektívy má model odpovedať.
- **Cieľ** – aký konkrétny výsledok chcete dostať.
- **Kroky** – ako má model postupovať.
- **Obmedzenia** – pre koho odpoveď je, aký má mať tón, dĺžku a čomu sa má vyhnúť.
- **Formát** – ako má byť odpoveď štruktúrovaná.
- **Vstupy** – texty alebo dáta, s ktorými má model pracovať.

## Praktická poznámka

Pri práci s cudzím textom, webom, e-mailami alebo dokumentmi je dobré oddeliť pravidlá od vstupných dát. Vstupný text môže obsahovať nedôveryhodné inštrukcie, napríklad pokus o prompt injection.
