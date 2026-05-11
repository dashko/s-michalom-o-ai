# Praktické tipy v tabuľke

Tento súbor obsahuje skrátený prehľad tipov z epizódy v tabuľke. Hodí sa ako rýchly copy/paste cheat sheet.

| Kategória | Tip | Názov | Na čo a prečo | Prompt SK (copy/paste) | Prompt EN (copy/paste) |
|---|---|---|---|---|---|
| Perspektíva | 1 | Zmeň rolu | Viac uhlov pohľadu k tej istej téme; rola mení dôraz, priority a štýl. | „Odpovedz ako senior expert. Potom ako skeptický reviewer: nájdi slabiny a riziká." | "Answer as a senior expert. Then as a skeptical reviewer: identify weaknesses and risks." |
| Perspektíva | 2 | Zmeň publikum | Keď ten istý obsah potrebuje CEO/QA/laik; zmenia sa dôrazy a forma. | „Napíš to pre: (1) CEO – 5 viet, (2) QA – checklist, (3) nováčika – krok za krokom." | "Write for: (1) CEO – 5 sentences, (2) QA – checklist, (3) beginner – step by step." |
| Výstup | 3 | Tón a hĺbka | Keď chceš riadiť tón, abstrakciu a mieru detailu. | „Buď stručný, vecný, bez metafor. Pridaj 3 najčastejšie chyby." | "Be concise, factual, no metaphors. Add the 3 most common mistakes." |
| Výstup | 4 | Daj to do šablóny | Na konzistentný výstup; porovnanie odpovedí, kopírovanie do nástrojov. | „Vráť odpoveď: Nadpis, TL;DR (3 body), Kroky, Riziká, Otázky." | "Return: Title, TL;DR (3 bullets), Steps, Risks, Questions." |
| Výstup | 5 | Povedz, čo nechceš | Znižuje šum; funguje keď je to konkrétne a merateľné. | „Nevysvetľuj teóriu. Neopakuj zadanie. Max 8 bodov." | "Don't explain theory. Don't repeat the prompt. Max 8 points." |
| Zadanie | 6 | Kontext + obmedzenia | Znižuje halucinovanie; zvyšuje relevantnosť a praktickosť. | „Kontext: … Cieľ: … Obmedzenia: čas 2 h, rozpočet 0 €, len Windows." | "Context: … Goal: … Constraints: time 2h, budget €0, Windows only." |
| Zadanie | 7 | Spýtaj sa na 3 veci | Keď chýbajú kľúčové parametre; zníži riziko zlého smeru. | „Polož max 3 otázky, bez ktorých nemôžeš pokračovať. Potom pokračuj s predpokladmi." | "Ask max 3 questions you can't proceed without. Then continue with assumptions." |
| Zadanie | 8 | Tu je vzor (few-shot) | Najspoľahlivejšie na trafenie štýlu a formátu. | „Tu je vzor: … Teraz sprav to isté pre môj prípad: …" | "Here is a pattern: … Now do the same for my case: …" |
| Myslenie | 9 | Kritériá úspechu | Model nevie čo maximalizovať; poradie priorít = lepšie kompromisy. | „Priority: jednoduchosť (1) > bezpečnosť (2) > výkon (3)." | "Priorities: simplicity (1) > security (2) > performance (3)." |
| Myslenie | 10 | Krok po kroku (CoT/CoD) | Model rozmýšľa postupne; presnejší výstup, menej halucinácií. Pre non-reasoning modely. | „Rozdeľ úlohu na 3–5 krokov. Pre každý: (1) čo spravíš, (2) pochybnosti, (3) čo je isté. Zhrnutie." | "Break into 3–5 steps. For each: (1) what you do, (2) doubts, (3) what is certain. Summary." |
| Myslenie | 11 | Porovnaj a vyber | Kontrast vytiahne slabé miesta; divergencia + konvergencia cez skórovanie. | „5 pre / 5 proti / 3 alternatívy. Potom odporúčanie." alebo „6 možností → 4 kritériá → ohodnoť 1–5 → top 2." | "5 pros / 5 cons / 3 alternatives. Then recommendation." or "6 options → 4 criteria → rate 1–5 → top 2." |
| Myslenie | 12 | Rozdeľ podľa času | Oddelí quick wins od systémových zmien; strategické uvažovanie. | „0–3 m, 3–12 m, 1–3 r: cieľ, kroky, riziká." | "0–3m, 3–12m, 1–3y: goal, steps, risks." |
| Kontrola | 13 | Iteruj s QA | Prvé kolo na obsah, druhé na opravy; checklist + čo chýba. | „V1: odpovedz. QA checklist (6 bodov). V2: oprav nálezy." | "V1: answer. QA checklist (6 points). V2: fix findings." |
| Kontrola | 14 | Predpoklady a istota | Brzda proti halucináciám; oddelí fakty od odhadov. | „Rozdeľ: (1) isté, (2) predpoklady, (3) čo overiť. Nevymýšľaj čísla." | "Split: (1) certain, (2) assumptions, (3) to verify. Don't invent numbers." |
| Kontrola | 15 | Nájdi slabiny a oprav | Nie „zlepši všeobecne" ale „tu je chyba → tu je oprava". | „Cituj 1–3 chyby. Max 5 slabín → spresni. Zmeň rady na konkrétne kroky." | "Quote 1–3 errors. Max 5 weaknesses → clarify. Turn advice into concrete steps." |
| Kontrola | 16 | 2 recenzenti (review) | Simuluje peer review; dva nezávislé pohľady odhalia viac. | „Reviewer A: riziká. Reviewer B: realizovateľnosť. Potom syntéza." | "Reviewer A: risks. Reviewer B: feasibility. Then synthesis." |
| Bonus | B | Zopakuj prompt | Zvyšuje kvalitu pri non-reasoning modeloch. Zdvojnásobí tokeny. | Skopíruj prompt pod seba 2×. | Copy the prompt below itself 2×. |
