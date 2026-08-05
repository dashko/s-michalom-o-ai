# Agentový cyklus: plan, act, observe, verify

Najdôležitejšia myšlienka pri agentovom programovaní je cyklus. Agent neodpovie len jednou správou. Postupne plánuje, koná, sleduje výsledok, kontroluje chyby a podľa toho upravuje ďalší krok.

Pri coding agentovi to môže vyzerať takto:

1. prečíta zadanie,
2. nájde relevantné súbory,
3. navrhne plán,
4. upraví kód,
5. spustí testy alebo build,
6. prečíta chybu,
7. opraví chybu,
8. ukáže diff alebo pripraví commit.

Toto je hlavný rozdiel medzi modelom a agentom. Model generuje odpoveď. Agent riadi pracovný postup.

## Agent nie je hotový, keď vygeneruje kód

Cieľom nie je dostať nejaký kód. Cieľom je dostať zmenu, ktorá prejde kontrolou.

Preto dobrý agent po sebe spustí testy, typecheck, lint alebo build. Ak testy padnú, agent by nemal skončiť vetou „hotovo". Mal by chybu prečítať, opraviť a skúsiť to znova.

Toto je rozdiel medzi generovaním kódu a agentovým programovaním.

## Kritériá úspechu

Pri agentoch nestačí povedať iba „sprav feature". Musíme povedať aj to, podľa čoho zistíme, že je feature hotová. Napríklad:

1. endpoint existuje,
2. test prejde,
3. UI flow funguje,
4. build je zelený,
5. a diff neobsahuje unrelated zmeny.

Agent potrebuje cieľ. Ale ešte viac potrebuje definíciu úspechu. Bez toho môže odpoveď vyzerať presvedčivo, ale výsledok nemusí byť použiteľný.

## Tool results sú ground truth

Pri agentovom programovaní neveríme len textu modelu. Dôležitejší je výsledok nástroja.

Ak test padol, tak padol. Ak build neprešiel, nie je hotovo. Ak súbor neexistuje, agent nemá predstierať, že existuje.

Agent je silný práve preto, že sa vie oprieť o realitu cez nástroje. Preto chceme, aby čítal výstupy testov, buildov, lintov, git diffov a logov. Model môže znieť sebavedomo. Tool output je zdroj pravdy.

## Diff je hlavný review artefakt

Pri coding agentovi nie je hlavný výstup pekná správa v chate. Hlavný výstup je diff.

Preto po agentovi nekontrolujeme iba jeho zhrnutie. Kontrolujeme, čo sa reálne zmenilo v súboroch. Agent môže povedať, že spravil malú zmenu. Ale `git diff` ukáže, či naozaj zmenil iba to, čo mal.

Praktické pravidlo: chat je vysvetlenie, diff je dôkaz.
