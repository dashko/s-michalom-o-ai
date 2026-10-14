# Jeden agent na všetko

V minulých dieloch sme agentovi nedávali jedno veľké zadanie, ale menšie a overiteľné kroky. A každý krok sme museli riadiť ručne: pozrieť diff, spustiť kontrolu, napísať ďalší prompt.

Keď takto agenta riadil človek, problém bol jeden: človek bol v cykle.

Na začiatku to trvalo minútu. Ale čím väčšia úloha, tým viac iterácií potrebuje človek spraviť, tým viac času to stálo.

A bol tu ešte druhý problém.

## Agent si potvrdzuje vlastnú prácu

Keď agent napíše riešenie a potom si ho sám skontroluje, kontroluje ho s rovnakými predpokladmi, rovnakým kontextom a rovnakým smerom myslenia.

Ak si pri písaní niečo vybral, má tendenciu si to pri reviewe potvrdiť. Nie preto, že by bol zlý, ale preto, že hľadá dôvody, prečo to funguje. A ten istý kontext, v ktorom chybu urobil, ju často ani nevidí.

## Babysitting

Agent dokončí krok. Ja sa pozriem. Poviem mu, čo má opraviť. On to spraví. Ja sa opäť pozriem.

Každá iterácia je fajn. Desiatky iterácií už nie. Človek sa stratí, zabudne, čo vlastne chcel, a postupne začne akceptovať akékoľvek riešenie, ktoré sa mu zdá dobré.

Toto je problém, ktorý v tejto epizóde odstránime: rozdelíme prácu na špecializovaných subagentov a cyklus ponecháme bežať bez nás.
