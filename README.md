# Kto w Polsce kupuje AI za publiczne pieniądze

Otwarty zbiór danych o ogłoszeniach o zamówieniach w Polsce, których przedmiot dotyczy
sztucznej inteligencji. Budowany codziennie, aktualizacja: **2026-09-02**.

Okres objęty zbiorem: **2026-05-12 do 2026-09-01**.

## Główne liczby

- Ogłoszeń przeanalizowanych (po filtrze słów-kluczy): **2349**
- Ogłoszeń, których przedmiot **naprawdę** dotyczy AI: **145** (6,2%)
- Ogłoszonych przez podmioty publiczne: **66**
- Różnych zamawiających: **106**

Pierwszy wniosek jest ostrzeżeniem: surowe wyszukiwanie po frazie „sztuczna inteligencja"
zawyża rynek kilkukrotnie. Większość trafień to zbiegi słów, nie zakupy AI.

## Skąd dane

| Rejestr | Co zawiera | Ogłoszeń o AI |
|---|---|---:|
| [Baza Konkurencyjności](https://bazakonkurencyjnosci.funduszeeuropejskie.gov.pl/) | ogłoszenia o zamówieniach w projektach współfinansowanych z funduszy europejskich | 98 |
| [TED (Tenders Electronic Daily)](https://ted.europa.eu/) | unijny dziennik zamówień publicznych, polska część | 36 |
| [eZamówienia](https://ezamowienia.gov.pl/) | krajowa platforma zamówień publicznych | 11 |

Największa część zbioru pochodzi z Bazy Konkurencyjności, gdzie ogłoszenia publikują beneficjenci
projektów unijnych, w tym firmy prywatne i fundacje. Nie jest to więc wyłącznie obraz przetargów
publicznych w rozumieniu prawa zamówień publicznych, tylko szerszy obraz zakupów finansowanych
ze środków publicznych. Kto pisze o „przetargach publicznych na AI" na podstawie tego zbioru,
pisze nieściśle.

## Kto kupuje

| Sektor | Ogłoszeń | Udział | Zamawiających |
|---|---:|---:|---:|
| Firmy prywatne | 70 | 48,3% | 46 |
| Uczelnie i instytuty | 28 | 19,3% | 23 |
| Ochrona zdrowia | 18 | 12,4% | 14 |
| Administracja centralna | 8 | 5,5% | 7 |
| Organizacje pozarządowe | 8 | 5,5% | 5 |
| Samorząd | 5 | 3,4% | 5 |
| Służby i wojsko | 4 | 2,8% | 3 |
| Oświata | 2 | 1,4% | 1 |
| Pozostałe | 1 | 0,7% | 1 |
| Spółki komunalne | 1 | 0,7% | 1 |

## Co kupują

| Rodzaj zamówienia | Ogłoszeń |
|---|---:|
| Wdrożenie systemu AI | 69 |
| Badania i rozwój | 28 |
| Szkolenia | 22 |
| Sprzęt (serwery, GPU, stacje) | 15 |
| Usługi IT bez AI | 6 |
| Licencje i gotowe oprogramowanie | 4 |
| Pozostałe | 1 |

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

> redAi, *Monitor AI w polskich zamówieniach finansowanych ze środków publicznych*, dane za okres 2026-05-12 do 2026-09-01,
> aktualizacja 2026-09-02. https://redai.pl/raport/kto-kupuje-ai-w-polsce
