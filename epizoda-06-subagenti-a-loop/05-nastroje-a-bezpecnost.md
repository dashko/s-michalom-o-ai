# Nástroje a bezpečnosť

Každý subagent môže mať prístup k iným nástrojom. Je to dôležité, lebo tým určujeme, čo smie robiť.

## Read-only reviewer

V našom deme má reviewer iba nástroje na čítanie:

- `read_file`,
- `grep_search`,
- `glob`,
- `list_directory`.

Nemá `edit`, `write_file`, ani `run_shell_command`. To znamená, že nemôže meniť kód, spúšťať testy ani zapisovať do súborov.

Prečo? Lebo jeho úlohou je dať verdict, nie riešiť problém. Ak by mohol meniť kód, mohol by problém "opraviť" namiesto toho, aby ho označil. Review, ktorý mení, už nie je review.

## Implementátor s plným prístupom

Implementátor má nástroje, ktoré potrebuje:

- čítanie a zmeny súborov (`read_file`, `edit`, `write_file`),
- vyhľadávanie (`grep_search`, `glob`, `list_directory`),
- spúšťanie commandov (`run_shell_command`).

## Prečo to je dôležité

Rozdelenie nástrojov je bezpečnostná hranica:

1. **Viditeľný review.** Reviewer nemôže zmeniť výsledok, jeho práca je transparentná a dá sa overiť.
2. **Malý blast radius.** Zmeny robí len agent, ktorý je na to pripravený.
3. **Jednoduchšia kontrola.** Keď má presná úloha presnú sadu nástrojov, je ľahšie zistiť, čo agent urobil a čo nie.

## Praktické pravidlo

Výber nástrojov je výber hraníc. Každému subagentovi dávame len tie nástroje, ktoré na jeho úlohu potrebuje: nič viac!
