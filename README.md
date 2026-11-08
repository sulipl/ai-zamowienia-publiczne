# Kto w Polsce kupuje AI za publiczne pieniądze

Otwarty zbiór danych o ogłoszeniach o zamówieniach w Polsce, których przedmiot dotyczy
sztucznej inteligencji. Budowany codziennie, aktualizacja: **2026-11-08**.

Okres objęty zbiorem: **2026-05-12 do 2026-11-07**.

## Główne liczby

- Ogłoszeń przeanalizowanych (po filtrze słów-kluczy): **4114**
- Ogłoszeń, których przedmiot **naprawdę** dotyczy AI: **246** (6%)
- Ogłoszonych przez podmioty publiczne: **104**
- Różnych zamawiających: **172**

Pierwszy wniosek jest ostrzeżeniem: surowe wyszukiwanie po frazie „sztuczna inteligencja"
zawyża rynek kilkukrotnie. Większość trafień to zbiegi słów, nie zakupy AI.

## Skąd dane

| Rejestr | Co zawiera | Ogłoszeń o AI |
|---|---|---:|
| [Baza Konkurencyjności](https://bazakonkurencyjnosci.funduszeeuropejskie.gov.pl/) | ogłoszenia o zamówieniach w projektach współfinansowanych z funduszy europejskich | 172 |
| [TED (Tenders Electronic Daily)](https://ted.europa.eu/) | unijny dziennik zamówień publicznych, polska część | 48 |
| [eZamówienia](https://ezamowienia.gov.pl/) | krajowa platforma zamówień publicznych | 26 |

Największa część zbioru pochodzi z Bazy Konkurencyjności, gdzie ogłoszenia publikują beneficjenci
projektów unijnych, w tym firmy prywatne i fundacje. Nie jest to więc wyłącznie obraz przetargów
publicznych w rozumieniu prawa zamówień publicznych, tylko szerszy obraz zakupów finansowanych
ze środków publicznych. Kto pisze o „przetargach publicznych na AI" na podstawie tego zbioru,
pisze nieściśle.

## Kto kupuje

| Sektor | Ogłoszeń | Udział | Zamawiających |
|---|---:|---:|---:|
| Firmy prywatne | 123 | 50% | 76 |
| Uczelnie i instytuty | 49 | 19,9% | 38 |
| Ochrona zdrowia | 20 | 8,1% | 16 |
| Organizacje pozarządowe | 15 | 6,1% | 8 |
| Samorząd | 14 | 5,7% | 12 |
| Administracja centralna | 11 | 4,5% | 10 |
| Służby i wojsko | 5 | 2% | 4 |
| Pozostałe | 4 | 1,6% | 4 |
| Oświata | 4 | 1,6% | 3 |
| Spółki komunalne | 1 | 0,4% | 1 |

## Co kupują

| Rodzaj zamówienia | Ogłoszeń |
|---|---:|
| Wdrożenie systemu AI | 90 |
| Badania i rozwój | 49 |
| Szkolenia | 46 |
| Sprzęt (serwery, GPU, stacje) | 34 |
| Licencje i gotowe oprogramowanie | 14 |
| Usługi IT bez AI | 11 |
| Pozostałe | 2 |

## Pliki

| Plik | Zawartość |
|---|---|
| `ai-zamowienia-publiczne.csv` | rekord na ogłoszenie, z sektorem i rodzajem zamówienia |
| `ai-zamowienia-publiczne.json` | agregaty i słowniki kodów |

Kolumny CSV: `data_publikacji`, `zamawiajacy`, `sektor`, `rodzaj_zamowienia`,
`dotyczy_ai` (0/1), `przedmiot`, `zrodlo`, `url`.

## Metodyka

**Źródła.** Trzy jawne rejestry wymienione wyżej. Skan działa codziennie, z oknem publikacji
obejmującym ostatnie trzy tygodnie.

**Filtr wstępny.** Ogłoszenie wchodzi do zbioru, jeśli zawiera jedno ze słów-kluczy o AI
i automatyzacji: sztuczna inteligencja, chatbot, voicebot, uczenie maszynowe, przetwarzanie
języka naturalnego, rozpoznawanie mowy, modele językowe, automatyzacja procesów i pokrewne.

**Deduplikacja.** Klucz to para zamawiający plus przedmiot zamówienia. Sprostowania
i powtórne publikacje tego samego ogłoszenia liczone są raz.

**Klasyfikacja.** Każde unikalne ogłoszenie opisane jest trzema cechami: sektor zamawiającego
(rozpoznawany po nazwie instytucji), rodzaj zamówienia oraz odpowiedź na pytanie, czy przedmiot
naprawdę dotyczy AI. Klasyfikację wykonuje model językowy, bo setki różnych nazw instytucji
nie daje się rozdzielić słowami-kluczami: część szpitali występuje pod nazwami spółek,
część urzędów pod nazwami własnymi.

**Czego tu nie ma.** Wartości zamówień. Ogłoszenia na etapie publikacji zwykle jej nie podają,
a szacowanie kwot z opisu byłoby zgadywaniem. Zbiór liczy ogłoszenia i zamawiających.

**Ograniczenia.** Zbiór obejmuje wyłącznie ogłoszenia, które trafiły w filtr słów-kluczy.
Postępowanie na system AI opisane wyłącznie językiem branżowym nie wejdzie do zbioru.
Okres jest krótki, więc dane pokazują strukturę rynku, a nie trend roczny.
Klasyfikacja modelem językowym ma niezerowy błąd; kolumna `dotyczy_ai` jest oceną, nie faktem urzędowym.

## Licencja i cytowanie

Dane pochodzą z jawnych rejestrów zamówień publicznych. Opracowanie udostępniamy na licencji
**CC BY 4.0**.

> redAi, *Monitor AI w polskich zamówieniach finansowanych ze środków publicznych*, dane za okres 2026-05-12 do 2026-11-07,
> aktualizacja 2026-11-08. https://redai.pl/raport/kto-kupuje-ai-w-polsce
