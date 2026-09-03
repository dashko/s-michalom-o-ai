# Testovanie LLM výstupu: LLM-as-a-judge

Klasický unit test porovnáva hodnoty. `expect(result).toBe(expected)`. To nefunguje, ak očakávaný výstup generuje LLM model. Každé volanie modelu môže vrátiť iný text. Chceme teda overiť, že variabilný výstup je správny, nie že sedí riadko za riadkom s nejakým reference textom.

Prístup v deme je LLM-as-a-judge.

## Ako to funguje

Test volá `summarize_git_diff` s malým vzorkovým git diff. Dostane výsledok. Potom volá druhý reálny Ollama endpoint a pýta ho, či výsledok:

- sedí na diff,
- obsahuje headline,
- snaží sa byť vtipný,
- obsahuje stručný technický súhrn.

Toto druhé volanie je judge. Vracia verdict, podľa ktorého test overí, či je výsledok prijemný.

```text
# Pseudokód
result = summarize_git_diff(sample_diff, "")
verdict = judge_call(
    prompt="Je tento výstup relevantný, má headline, snáži sa byť vtipný a obsahuje stručný súhrn?",
    input=result,
)
assert verdict.passed
```

## Prečo bez mockov

Mock by nám ukázal, že kód nie je syntakticky zlý a že sa správne volá. Ale nezistí, čo model naozaj produkuje. Pri LLM-as-a-judge testy chceme vedieť, či reálne volanie do modelu dáva výsledok, ktorý dáva zmysel.

Tento prístup má aj slabinu. Výsledok závisí od stability modelu a od toho, ako je napísaný prompt pre judge. Preto je dôležité:

- udržiavať prompt pre judge stabilný a jasný,
- testy spúšťať na rovnakom modeli ako hlavné volanie,
- ak model alebo endpoint nie sú nakonfigurované, test má padnúť.

## Praktické pravidlo

Ak má aplikácia LLM ako zdroj dát, test by mal overiť, že daný LLM výstup sedí na zadanie, nie že sedí na reference text. LLM-as-a-judge je praktická cesta, ako to urobiť bez manuálnej kontroly.
