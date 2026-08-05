# Nastavenie modelu: Ollama a Qwen Code

V praktickej časti používame Qwen Code ako coding agenta priamo nad projektom. Pointou nie je ukázať, že model vie písať kód, ale ukázať workflow:

1. dáme agentovi jasné zadanie,
2. agent si načíta relevantné súbory,
3. pripraví plán,
4. spraví zmenu,
5. spustí kontrolu,
6. a na konci ukáže, čo zmenil.

Presne toto odlišuje agentové programovanie od obyčajného kopírovania kódu z chatu.

## Nastavenie Ollamy

Model beží cez Ollamu. Ollama nám slúži ako lokálny alebo self-hosted model server, ku ktorému sa Qwen Code pripája cez OpenAI-compatible API.

Pri agentoch je dôležité, aby bol model nastavený konzistentne. Nechceme, aby sa raz správal veľmi kreatívne a inokedy veľmi deterministicky. Preto nastavujeme kontext, sampling parametre, GPU vrstvy a cache tak, aby bol model použiteľný na dlhšie coding úlohy.

```bash
OLLAMA_HOST=10.8.0.2
CUDA_VISIBLE_DEVICES=0,1,2,3         # Používané GPU
OLLAMA_CONTEXT_LENGTH=98304          # Maximálna veľkosť kontextu
OLLAMA_FLASH_ATTENTION=1             # Flash Attention optimalizácia, rýchlejšie a úspornejšie spracovanie attention vrstiev
OLLAMA_KV_CACHE_TYPE=f16             # Typ KV cache kvantizácie pre nižšiu spotrebu VRAM
OLLAMA_MAX_LOADED_MODELS=1           # Max. počet načítaných modelov
OLLAMA_NUM_PARALLEL=1                # Počet paralelných požiadaviek
OLLAMA_GPU_LAYERS=999                # Počet vrstiev na GPU
OLLAMA_NO_MMAP=1                     # Vypnuté mmap načítanie modelov
OLLAMA_KEEP_ALIVE=-1                 # Neobmedzené držanie modelu v RAM, načítanie modelu priamo do RAM namiesto mmap z disku.
```

Konkrétnu definíciu modelu pre Ollamu nájdete v súbore [`qwen-coder.Modelfile`](./qwen-coder.Modelfile).

## Token budget a výstupný limit

Veľký kontext neznamená nekonečnú prácu. Aj keď máme 96K context, stále musíme rozmýšľať nad tým, čo do kontextu dávame. Každý súbor, log, diff a výstup testu zaberá miesto. Ak do kontextu nahádžeme celý projekt, agent môže mať síce veľa informácií, ale horšie rozlišuje, čo je dôležité.

Druhý limit je výstup. Model nemôže v jednej odpovedi spoľahlivo vygenerovať nekonečne veľa kódu. Preto je lepšie robiť menšie kroky:

- jeden súbor,
- jedna zmena,
- jeden test,
- jedna kontrola.

Toto je pri lokálnych modeloch veľmi praktické. Dobrý workflow je často dôležitejší než samotná veľkosť modelu.

## Nastavenie ~/.qwen/settings.json

Posledný krok je povedať Qwen Code, kde tento model nájde. Na to slúži `~/.qwen/settings.json`, kde nastavíme model provider, URL na Ollamu, autentifikáciu a defaultný model.

Qwen Code sa potom správa tak, ako keby volal OpenAI-compatible API, ale v skutočnosti ide na náš Ollama server. Samotný agent nemusí riešiť, či model beží lokálne, na inom serveri alebo cez API. Dôležité je, že má jednotné rozhranie.

```json
{
    "modelProviders": {
        "openai": [
            {
                "id": "qwen-coder",
                "name": "qwen-coder",
                "envKey": "OLLAMA_API_KEY",
                "baseUrl": "https://ollama.example.com/v1",
                "generationConfig": {
                    "timeout": 60000,
                    "maxRetries": 3,
                    "samplingParams": {
                        "temperature": 0.15,
                        "top_p": 0.9,
                        "repeat_penalty": 1.05,
                        "max_tokens": 65536
                    }
                }
            }
        ]
    },
    "security": {
        "auth": {
            "selectedType": "openai"
        }
    },
    "model": {
        "name": "qwen-coder"
    },
    "env": {
        "OLLAMA_API_KEY": ...
    }
}
```

Keď je toto nastavené, Qwen Code už vie, aký model má používať a kam má posielať požiadavky. Od tejto chvíle sa môžeme sústrediť na samotný workflow, nie na ručné prepínanie modelov a endpointov.

## Režimy práce v Qwen Code

Qwen Code môžete spustiť v interaktívnom režime a potom používať `@` na referencovanie súborov. Agent ich okamžite načíta do kontextu a môžete s nimi pracovať ako súčasťou rozhovoru.

Tabulátorom si zmeníme režim. Plan mode nám pomôže najprv naplánovať implementáciu a až potom začať meniť súbory.

## Read-only fáza

Dobrý agent by nemal hneď začať meniť kód. Najprv by mal pochopiť projekt. Prakticky to znamená:

1. pozrie štruktúru projektu,
2. nájde relevantné súbory,
3. zistí test command,
4. pochopí existujúci pattern,
5. navrhne plán,
6. a až potom edituje.

Toto je veľmi dôležité hlavne v cudzom projekte. Ak agent začne písať kód skôr, než pochopí kontext, často vyrobí zmenu, ktorá síce vyzerá správne, ale nezapadne do projektu.
