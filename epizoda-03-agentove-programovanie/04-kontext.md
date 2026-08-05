# Kontext pri agentoch

Agent môže mať nástroje, plán aj dobrý model, ale ak dostane zlý alebo príliš veľký kontext, výsledok bude horší.

## Kontext nie je nekonečná pamäť

Aj keď máme veľké kontextové okno, neznamená to, že doň máme nahádzať celý projekt. Čím viac nesúvisiaceho textu agent dostane, tým väčšia šanca, že sa stratí alebo začne riešiť nepodstatné veci.

Dobrý agentový workflow je preto hlavne o tom, že agentovi dávame správny kontext v správnom čase. Nie celý projekt. Nie všetky logy. Nie všetky pravidlá firmy. Len to, čo potrebuje na aktuálnu úlohu.

## Context hygiene

Pri agentoch nie je cieľom naplniť kontext. Cieľom je dať agentovi najmenší užitočný kontext, ktorý potrebuje na aktuálnu úlohu. Toto je context hygiene.

Zlý kontext je napríklad:

- príliš veľa nesúvisiacich súborov,
- staré logy,
- obrovský diff,
- dlhý AGENTS.md plný všeobecných pravidiel,
- dokumentácia, ktorá nesúvisí s aktuálnou zmenou.

Čím viac šumu agent dostane, tým ťažšie rozlišuje, čo je dôležité. Preto je lepšie povedať:

```text
Pozri iba tieto tri súbory a existujúce testy okolo tejto funkcionality.
```

Nie:

```text
Tu máš celý projekt, oprav bug.
```

## Context compression v Qwen Code

Aj keď si dávame pozor na kontext, pri dlhšej práci sa chat postupne zapĺňa. Agent číta súbory, spúšťa testy, dostáva chyby, opravuje kód a každý krok zaberá miesto v kontexte.

Qwen Code preto vie použiť context compression: staršiu časť konverzácie zhrnie do kratšej podoby, aby sa uvoľnilo miesto pre ďalšiu prácu. Je to užitočné hlavne pri dlhých agentických taskoch, napríklad keď agent najprv analyzuje projekt, potom implementuje feature, potom opravuje testy a nakoniec pripravuje diff.

Praktické pravidlo: context compression pomáha pokračovať v dlhej práci, ale nenahrádza dobrý prompt, dobrý plán a malé overiteľné kroky.

## Informačná architektúra agenta

Pri agentoch je dôležité nemiešať všetko do jedného promptu. Preto je dobré rozmýšľať nad tým, kam ktorý typ informácie patrí.

- Stabilné pravidlá projektu patria do AGENTS.md alebo QWEN.md: coding style, test commandy, pravidlá pre dependency, branch workflow alebo verification checklist.
- Aktuálne zadanie patrí do promptu: cieľ, konkrétne výstupy, obmedzenia a kritériá úspechu pre aktuálnu úlohu.
- Relevantné súbory, logy a diff patria do kontextu aktuálnej úlohy. Nie celý projekt, ale iba to, čo agent potrebuje práve teraz.
- Opakovateľné postupy patria do skillov: práca s Excelom, generovanie reportu, code review checklist alebo špecifický firemný postup.
- Externé systémy a nástroje patria do MCP: databáza, Jira, CRM, interné API alebo vyhľadávanie.
- Úzke delegované úlohy patria subagentom: napríklad keď hlavný agent potrebuje, aby niekto samostatne pozrel diff, našiel relevantné súbory alebo pripravil krátky review kontext.

Keď toto oddelíme, agent sa správa stabilnejšie. Nedostáva jeden obrovský zmiešaný prompt, ale správny typ informácie na správnom mieste.
