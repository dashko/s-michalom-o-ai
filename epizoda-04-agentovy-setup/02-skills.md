# Skills: rozšírenie agentových schopností

Keď agent potrebuje špecifickú schopnosť iba občas, použijeme skill. Skill je malý návod alebo balík schopností, ktorý agent zapne iba vtedy, keď ho potrebuje.

Príklady:

- práca s Dockerom,
- práca s Excelom,
- code review checklist,
- generovanie reportu,
- používanie internej terminológie.

Výhoda je, že tieto pravidlá nemusíme držať stále v hlavnom kontexte. To je dôležité hlavne pri menších modeloch. Menší model má menšiu toleranciu na chaos v kontexte, preto je lepšie mať viac menších špecializovaných skillov než jeden obrovský systémový prompt.

## Kam patrí skill a kam AGENTS.md

Skill nie je miesto na všetko.

- Ak informácia patrí len k jednému projektu, dáme ju skôr do AGENTS.md.
- Ak je to opakovateľná schopnosť naprieč projektmi, dáva zmysel ako skill.

Skills sú teda dobré na opakovateľné postupy: ako pracovať s konkrétnym CLI nástrojom, ako generovať dokument, ako robiť code review, ako pripraviť report alebo ako používať internú terminológiu.

## Autoskills

Ak používate Qwen Code, okrem práce s pamäťou automaticky vytvára aj skilly, teda autoskills. Opakujúce sa procesy a workflowy vie priebežne ukladať a neskôr znovu použiť.

## Kde hľadať hotové skilly

- [awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)
- [officialskills.sh](https://officialskills.sh/)

Ešte jedna možnosť, ako držať kontext menší, sú subagenti. Tým sa venujeme v praktickom deme v ďalšej časti, kde hlavný agent deleguje úzku úlohu na špecializovaného pomocníka.
