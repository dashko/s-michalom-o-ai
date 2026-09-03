# Agentový workflow: malý krok, kontrola, commit

Najväčšia chyba pri coding agentoch je pustiť ich na veľkú úlohu bez kontroly. Prompt typu „postav celú aplikáciu" znie lákavo, ale často skončí chaosom: veľa súborov, nejasný diff, padnuté testy a zmeny, ktoré sme nechceli.

Lepší prístup je agentový workflow. Malý prompt. Malý krok. Kontrola diffu. Test. Review. Commit. Až potom ďalší krok.

## Prečo jedno veľké zadanie nefunguje

Keď dostane agent „postav celú aplikáciu", začne hádať. Sám rozhodne architektúru, štruktúru súborov, závislosti, štýl. A nám je ťažké vedieť, kde končí jedno rozhodnutie a kde začína druhé. Diff nám ukáže veľa zmien naraz a nedokážeme povedať, ktorý riadok spôsobil ktorý problém.

## Čo je agentový workflow

Ten istý výsledok, len v krokoch:

1. Docker prostredie.
2. MCP server.
3. SQLite logovanie.
4. API + React UI.

Každý krok je samostatný prompt s jasným cieľom, požiadavkami a verification. Keď agent ukončí krok, nezadávame hneď ďalší. Najprv spravíme postup:

1. `git diff`,
2. review zmenených súborov,
3. test alebo inú verification kontrolu,
4. commit, ak je zmena dobrá.

Commit je checkpoint. Ak v ďalšom kroku agent niečo pokazí, vieme porovnať diff, revertovať zlý krok, alebo pokračovať z posledného dobrého stavu.

## Pravidlo

Agent môže iterovať rýchlo, ale každá iterácia musí skončiť reviewom a commitom. Bez toho sa po pár krokoch dostaneme do situácie, kde nevieme, ktorá zmena čo spôsobila. Vtedy už agent nepomáha, ale vyrába chaos.

## Rozdiel oproti vibe codingu

Toto je rozdiel medzi agentovým programovaním a vibe codingom, resp. púšťaním náhodného autopilota. Agent vie písať rýchlo. Človek ale musí robiť často review.
