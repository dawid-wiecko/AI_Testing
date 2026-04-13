# 📅 Miesiące 2–3 — Playwright Python + REST API + Docker + Portfolio #1

> **Cel**: Python golden stack + pierwsze projekty portfolio + aktywna rekrutacja  
> **Rezultat**: Masz kompletny automation stack wymagany przez setki firm (23–27k PLN B2B)

---

## 🔄 TYDZIEŃ 2.5 — Odświeżenie Języka: async/await + threading + type hints

> 📌 *Zanim wejdziesz w Playwright — musisz czuć się swobodnie z asyncio. Playwright Python jest w 100% async.*

**🎯 Opis ogólny**: Masz 8 lat doświadczenia z Pythonem i C# — ale wielowątkowość i programowanie asynchroniczne to obszary które wiele osób "zna w teorii, rzadko używa w praktyce". Playwright Python opiera się na `asyncio`, pytest-asyncio, `async def` i `await` — bez tego podstawy będziesz walczył z frameworkiem zamiast uczyć się testowania. C# background pomaga: `async/await` w C# i Pythonie to ten sam koncept, inna składnia.

**Dlaczego teraz, a nie później?**
- `playwright.async_api` = jedyna produkcyjna wersja Playwright Python
- Każdy fixture w pytest-playwright to `async def`
- `asyncio.gather()` = równoległe testy / równoległe requesty API
- Zrozumienie event loop wyjaśnia dlaczego `await` jest wymagane i co się stanie bez niego

---

### Dzień 1 — Python async/await i event loop

> 📌 *Coroutines, event loop, await — fundament Playwright Python*

**🎯 Cel bloku**: Rozumiesz czym jest coroutine, event loop i dlaczego `await` jest potrzebne

🕐 **BLOK 1 (45 min)** — Teoria: coroutines i event loop
- Materiał: [Real Python — Async IO](https://realpython.com/async-io-python/) — darmowy, kompleksowy
- Kluczowe koncepty:
  - `async def` → tworzy coroutine, NIE wywołuje jej od razu
  - `await` → "zatrzymaj tę coroutine, pozwól event loop robić inne rzeczy"
  - `asyncio.run()` → uruchamia event loop (entry point)
  - Różnica: `threading` (prawdziwa wielowątkowość) vs `asyncio` (kooperatywna wielozadaniowość)
- Porównanie z C# które już znasz:
  ```
  C#                              Python
  ──────────────────────────────────────────
  async Task DoWork()         →   async def do_work():
  await SomeMethod()          →   await some_method()
  Task.Run(() => ...)         →   asyncio.create_task(...)
  await Task.WhenAll(t1, t2)  →   await asyncio.gather(t1, t2)
  ```

☕ **PRZERWA (15 min)**

🕑 **BLOK 2 (45 min)** — Ćwiczenia: napisz swoje pierwsze coroutines
- Zadanie 1: napisz `async def fetch_user(id)` symulujące opóźnienie z `await asyncio.sleep(1)`
- Zadanie 2: uruchom 5 `fetch_user()` sekwencyjnie vs równolegle z `asyncio.gather()` — zmierz czas
- Zadanie 3: przepisz synchroniczną funkcję na async i sprawdź że działa
- Materiał pomocniczy: [Python asyncio docs](https://docs.python.org/3/library/asyncio.html)

📝 **PODSUMOWANIE (15 min)**
- [ ] Rozumiem różnicę `async def` vs zwykłej funkcji
- [ ] Wiem co robi `asyncio.gather()` i kiedy go użyć
- [ ] Uruchomiłem przykład gdzie gather() jest ~5× szybszy niż sekwencja
- [ ] Commit: `async_basics.py` z przykładami

---

### Dzień 2 — Python threading i concurrent.futures

> 📌 *threading dla I/O-bound tasks, ProcessPoolExecutor dla CPU-bound — plus pytest-xdist dla równoległych testów*

**🎯 Cel bloku**: Wiesz kiedy użyć threading vs asyncio vs multiprocessing w kontekście testów

🕐 **BLOK 1 (45 min)** — threading.Thread i concurrent.futures
- Materiał: [Real Python — Threading](https://realpython.com/intro-to-python-threading/) — darmowy
- Kluczowe koncepty:
  ```python
  # threading.Thread — podstawy
  import threading
  t = threading.Thread(target=my_function, args=(arg1,))
  t.start()
  t.join()  # czekaj na zakończenie

  # concurrent.futures — wygodniejsze API
  from concurrent.futures import ThreadPoolExecutor
  with ThreadPoolExecutor(max_workers=4) as executor:
      results = list(executor.map(test_api_endpoint, endpoints))
  ```
- **Thread safety** w testach — dlaczego Singleton driver jest NIEBEZPIECZNY przy `workers=4`:
  - Race condition: dwa testy modyfikują ten sam obiekt jednocześnie
  - Rozwiązanie: każdy worker ma swój driver (fixture scope="function")
- GIL (Global Interpreter Lock) — dlaczego CPU-bound kod NIE przyspiesza z threading

☕ **PRZERWA (15 min)**

🕑 **BLOK 2 (45 min)** — pytest-xdist: równoległe testy
- Materiał: [pytest-xdist docs](https://pytest-xdist.readthedocs.io/) — darmowy
- Instalacja: `pip install pytest-xdist`
- Użycie: `pytest -n 4` (4 workery równolegle)
- Zadanie: uruchom swój istniejący zestaw testów Selenium z `-n 4` i sprawdź:
  - Czy testy przechodzą? (race conditions?)
  - Ile razy szybciej? (prawo Amdahla w praktyce)
  - Co się psuje? (shared state, hardkodowane dane)
- Thread-safe fixtures pattern:
  ```python
  @pytest.fixture(scope="function")  # NIE "session" przy xdist!
  def driver():
      d = webdriver.Chrome()
      yield d
      d.quit()
  ```

📝 **PODSUMOWANIE (15 min)**
- [ ] Wiem kiedy użyć threading vs asyncio (I/O-bound vs event-driven)
- [ ] Uruchomiłem testy z pytest-xdist `-n 4`
- [ ] Rozumiem dlaczego Singleton driver jest problematyczny przy parallel testing
- [ ] Commit: notatka z wynikami porównania sequential vs parallel

---

### Dzień 3 — Python type hints + dataclasses (czytelność kodu testów)

> 📌 *Type hints nie są obowiązkowe w Pythonie, ale w 2026 są standardem w każdym profesjonalnym projekcie*

**🎯 Cel bloku**: Twój kod testowy ma type hints — wygląda profesjonalnie i działa z IDE autocompletion

🕐 **BLOK 1 (45 min)** — Type hints w Pythonie
- Materiał: [Python type hints docs](https://docs.python.org/3/library/typing.html) + [Real Python type checking](https://realpython.com/python-type-checking/)
- Kluczowe dla testów:
  ```python
  from typing import Optional, List, Dict, Generator
  from playwright.async_api import Page, Browser, BrowserContext

  # Fixture z type hint
  async def login_page(page: Page) -> LoginPage:
      return LoginPage(page)

  # Page Object z typami
  class LoginPage:
      def __init__(self, page: Page) -> None:
          self.page = page

      async def login(self, username: str, password: str) -> HomePage:
          await self.page.fill("#user", username)
          await self.page.fill("#pass", password)
          await self.page.click("#login")
          return HomePage(self.page)
  ```
- Dlaczego warto: IDE podpowiada metody, błędy wykrywane przed uruchomieniem

☕ **PRZERWA (15 min)**

🕑 **BLOK 2 (45 min)** — dataclasses dla danych testowych
- Materiał: [Python dataclasses docs](https://docs.python.org/3/library/dataclasses.html)
- Zastąpienie słowników w testach:
  ```python
  from dataclasses import dataclass, field
  from typing import Optional

  @dataclass
  class TestUser:
      username: str
      password: str
      role: str = "standard_user"
      email: Optional[str] = None

  # Zamiast: {"username": "standard_user", "password": "secret_sauce"}
  # Używaj:
  user = TestUser(username="standard_user", password="secret_sauce")
  admin = TestUser(username="admin", password="admin_pass", role="admin")
  ```
- Łączenie z Factory pattern (z poprzedniego tygodnia):
  ```python
  class UserFactory:
      @staticmethod
      def standard() -> TestUser:
          return TestUser(username="standard_user", password="secret_sauce")
      @staticmethod
      def admin() -> TestUser:
          return TestUser(username="admin_user", password="admin_pass", role="admin")
  ```
- Zadanie: przepisz swoje dane testowe z dict na dataclasses

📝 **PODSUMOWANIE (15 min)**
- [ ] Mam type hints na wszystkich fixture'ach i Page Objects
- [ ] Dane testowe używają dataclasses zamiast dict
- [ ] Połączyłem dataclasses z Factory pattern
- [ ] Commit: zaktualizowany kod z type hints

---

### Dzień 4 — C# async/await i Task (przypomnienie + porównanie z Pythonem)

> 📌 *Skoro znasz C# — utrwalenie async/await pomoże Ci w Playwright C# gdy przyjdzie czas*

**🎯 Cel bloku**: Czujesz się pewnie z async/await w C# i rozumiesz różnice vs Python asyncio

🕐 **BLOK 1 (45 min)** — C# Task, async/await, ConfigureAwait
- Materiał: [Microsoft async/await docs](https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/) — darmowy
- Kluczowe różnice Python asyncio vs C# async:
  ```
  Python asyncio                    C# async/await
  ────────────────────────────────────────────────
  Single-threaded event loop    →   Thread pool (Task Scheduler)
  asyncio.gather(t1, t2)        →   await Task.WhenAll(t1, t2)
  asyncio.create_task(coro())   →   Task.Run(() => Method())
  async for item in aiter():    →   await foreach (var item in aiter)
  No ConfigureAwait              →   ConfigureAwait(false) dla lib
  ```
- Pułapki C# async w testach:
  - `async void` → NIGDY w testach (wyjątki giną)
  - `Task.Result` / `.Wait()` → deadlock risk — ZAWSZE używaj `await`
  - xUnit i NUnit wspierają `async Task` testy natywnie

☕ **PRZERWA (15 min)**

🕑 **BLOK 2 (45 min)** — Playwright C# async pattern (podgląd)
- Materiał: [Playwright .NET docs](https://playwright.dev/dotnet/docs/intro) — darmowy
- Zobaczysz że Playwright C# wygląda znajomo:
  ```csharp
  [Test]
  public async Task LoginTest()
  {
      using var playwright = await Playwright.CreateAsync();
      await using var browser = await playwright.Chromium.LaunchAsync();
      var page = await browser.NewPageAsync();
      await page.GotoAsync("https://saucedemo.com");
      await page.FillAsync("#user-name", "standard_user");
      await page.ClickAsync("#login-button");
      await Expect(page).ToHaveTitleAsync("Swag Labs");
  }
  ```
- Zadanie: uruchom przykładowy test z dokumentacji Playwright .NET (nie musisz pisać własnego)

📝 **PODSUMOWANIE (15 min)**
- [ ] Rozumiem różnicę Python asyncio vs C# Task
- [ ] Wiem czemu `async void` jest niebezpieczne w testach C#
- [ ] Widziałem jak wygląda Playwright C# — API jest znajome
- [ ] Notatka: "Różnice async Python vs C# które warto pamiętać: ..."

---

### 📚 Zasoby uzupełniające — Concurrency

| Temat | Zasób | Poziom |
|-------|-------|--------|
| Python asyncio deep dive | [Real Python Async IO](https://realpython.com/async-io-python/) | Średni |
| Python threading | [Real Python Threading](https://realpython.com/intro-to-python-threading/) | Podstawy |
| Python type hints | [mypy cheatsheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html) | Podstawy |
| C# async/await | [Microsoft docs](https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/) | Podstawy |
| pytest-xdist | [Official docs](https://pytest-xdist.readthedocs.io/) | Praktyczny |
| Playwright asyncio integration | [playwright-python GitHub](https://github.com/microsoft/playwright-python) | Praktyczny |

---

### ✅ Checklist — Tydzień 2.5

- [ ] Napisałem i uruchomiłem `asyncio.gather()` z mierzeniem czasu
- [ ] Uruchomiłem testy z `pytest -n 4` i rozumiem wyniki
- [ ] Kod testowy ma type hints na fixture'ach i Page Objects
- [ ] Dane testowe używają `@dataclass` zamiast `dict`
- [ ] Rozumiem różnicę threading vs asyncio vs multiprocessing
- [ ] Znam pułapki parallel testing (thread safety, shared state)
- [ ] Widziałem Playwright C# async pattern

---

## 🐍 TYGODNIE 3–5: pytest Advanced + Playwright Python

> Kandydat zna Python — to skraca naukę Playwright **2–3×**. Po 3 tygodniach masz KOMPLETNY automation stack.
> ✅ **async/await już znasz** — Playwright Python będzie naturalne.

---

### 📅 TYDZIEŃ 3 — pytest Advanced (fixtures, conftest, parametrize)

### Dzień 15 — pytest Fixtures Zaawansowane
> 📌 *Fixtures scope, conftest.py — fundament skalowalnych projektów testowych*

**🎯 Cel bloku**: Rozumiesz scope fixtures (function/class/module/session) i używasz conftest.py

🕐 **BLOK 1 (45 min)** — Fixtures scope i conftest
- Materiał: [pytest fixtures docs](https://docs.pytest.org/en/stable/how-to/fixtures.html) — sekcje scope i conftest.py
- Zadanie: Przeczytaj dokumentację scope, napisz fixture w każdym z 4 scopów i zweryfikuj kiedy są wywoływane

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Refaktoryzacja testów Selenium
- Materiał: Twoje istniejące testy Selenium
- Zadanie: Przepisz 5 istniejących testów Selenium by używały fixtures (driver jako fixture, cleanup w finalizer)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz różnicę między scope="function" a scope="session"?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Napisałem fixtures we wszystkich 4 scopach, conftest.py działa

---

### Dzień 16 — pytest parametrize
> 📌 *Parametryzacja testów — jeden test, wiele scenariuszy*

**🎯 Cel bloku**: Piszesz testy parametryczne z @pytest.mark.parametrize

🕐 **BLOK 1 (45 min)** — parametrize teoria
- Materiał: [pytest parametrize docs](https://docs.pytest.org/en/stable/how-to/parametrize.html) — @pytest.mark.parametrize, indirect, IDs
- Zadanie: Napisz 3 przykłady: prosty, z tuple, z IDs

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Ćwiczenia parametryzacji
- Materiał: Twoje istniejące testy
- Zadanie: Napisz 3 testy parametryczne z 5+ przypadkami każdy (np. testy logowania z różnymi danymi)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy potrafisz sparametryzować test indirect fixtures?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Napisałem 3 testy parametryczne, każdy z 5+ przypadkami

---

### Dzień 17 — pytest Markers + Allure
> 📌 *Markery i raportowanie — kategorie testów i profesjonalne raporty*

**🎯 Cel bloku**: Własne markery, xfail, skip skonfigurowane; Allure raport generuje się lokalnie

🕐 **BLOK 1 (45 min)** — Markers i allure install
- Materiał: [pytest markers docs](https://docs.pytest.org/en/stable/how-to/mark.html) + [allure-pytest](https://allurereport.org/docs/pytest/)
- Zadanie: Zainstaluj allure-pytest (`pip install allure-pytest`), stwórz własne markery @smoke, @regression, @slow

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Konfiguracja Allure
- Materiał: [Allure pytest guide](https://allurereport.org/docs/pytest/)
- Zadanie: Skonfiguruj Allure report dla istniejących testów — dodaj @allure.title, @allure.description, @allure.step

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy `allure serve` generuje czytelny raport HTML?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Allure raport generuje się lokalnie z markerami

---

### Dzień 18 — conftest.py Architektura
> 📌 *Duże projekty testowe — hierarchia conftest.py na różnych poziomach*

**🎯 Cel bloku**: Tworzysz projekt z 3-poziomową hierarchią conftest.py

🕐 **BLOK 1 (45 min)** — Architektura conftest
- Materiał: [pytest conftest docs](https://docs.pytest.org/en/stable/reference/fixtures.html#conftest-py-sharing-fixtures-across-files)
- Zadanie: Przeczytaj dokumentację, narysuj (na papierze lub w Markdownie) strukturę katalogu z konfiguracją conftest na każdym poziomie

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Implementacja struktury
- Materiał: Własna implementacja
- Zadanie: Stwórz strukturę projektu: `tests/` (root conftest), `tests/ui/` (UI conftest), `tests/api/` (API conftest) z fixtures na każdym poziomie

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy fixture z root conftest jest dostępny w podkatalogach?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Projekt z 3 poziomami conftest.py działa poprawnie

---

### Dzień 19 — pytest-html + Coverage
> 📌 *HTML raporty i pomiar pokrycia kodu testami*

**🎯 Cel bloku**: HTML raport i coverage report generują się automatycznie po każdym uruchomieniu

🕐 **BLOK 1 (45 min)** — pytest-html i pytest-cov
- Materiał: [pytest-html docs](https://pytest-html.readthedocs.io/) + [pytest-cov docs](https://pytest-cov.readthedocs.io/)
- Zadanie: `pip install pytest-html pytest-cov`, skonfiguruj `pytest.ini` lub `pyproject.toml` z opcjami raportowania

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Integracja z projektem
- Materiał: Twój projekt testowy
- Zadanie: Dodaj HTML report + coverage do projektu, sprawdź procent pokrycia, zidentyfikuj niepokryte linie

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy `pytest --html=report.html --cov` działa bez błędów?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Coverage report pokazuje >80%, HTML raport generuje się automatycznie

---

### Dzień 20 — Review pytest + Mini Projekt README
> 📌 *Konsolidacja tygodnia — dokumentacja projektu*

**🎯 Cel bloku**: Mini projekt pytest z pełną dokumentacją gotowy na GitHub

🕐 **BLOK 1 (45 min)** — Uzupełnienie luk
- Materiał: Notatki z tygodnia 3
- Zadanie: Przejrzyj wszystkie tematy, uzupełnij luki, napisz 5 dodatkowych testów używających wszystkich poznanych technik

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — README i dokumentacja
- Materiał: Przykłady README na GitHub
- Zadanie: Napisz README dla mini projektu: opis, tech stack badges, instrukcja uruchomienia, opis struktury

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy ktoś nieznający projektu mógłby go uruchomić korzystając tylko z README?
- [ ] Commit i push na GitHub
- [ ] Checkpoint: - [ ] README kompletny, projekt widoczny publicznie na GitHub

---

### Dzień 21 — Refaktoryzacja Testów Selenium
> 📌 *Modernizacja istniejących testów — zastosowanie całej wiedzy z tygodnia 3*

**🎯 Cel bloku**: 10 testów Selenium przepisanych z pytest fixtures, markers, parametrize

🕐 **BLOK 1 (45 min)** — Analiza i planowanie
- Materiał: Twoje istniejące testy Selenium
- Zadanie: Wybierz 10 testów do refaktoryzacji, zaplanuj: jakie fixtures, jakie markery, co parametryzować

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Implementacja refaktoryzacji
- Materiał: Dokumentacja pytest (do podglądu)
- Zadanie: Przepisz 10 wybranych testów — fixtures, conftest, parametrize, markers, Allure dekoratory

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy stare testy przechodzą po refaktoryzacji?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 10 testów Selenium przepisanych z pełnym pytest stack

---

## 📅 TYDZIEŃ 4 — Playwright Python — Podstawy

### Dzień 22 — Instalacja i Pierwszy Test
> 📌 *Playwright dla Python — nowoczesny framework UI automation*

**🎯 Cel bloku**: Playwright zainstalowany, pierwszy test przechodzi w 3 przeglądarkach

🕐 **BLOK 1 (45 min)** — Instalacja i konfiguracja
- Materiał: [Playwright Python — Getting Started](https://playwright.dev/python/docs/intro)
- Zadanie: `pip install playwright`, `playwright install`, napisz pierwszy test otwierający stronę

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Pierwsze testy w 3 przeglądarkach
- Materiał: [Playwright Python docs — browsers](https://playwright.dev/python/docs/browsers)
- Zadanie: Uruchom test w chromium, firefox, webkit — zrozum różnice w konfiguracji

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy testy przechodzą we wszystkich 3 przeglądarkach?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Playwright działa, pierwszy test przechodzi w chromium/firefox/webkit

---

### Dzień 23 — Locators
> 📌 *Selektory Playwright — jak znajdować elementy na stronie (lepiej niż XPath)*

**🎯 Cel bloku**: Używasz get_by_role, get_by_text, get_by_label zamiast kruchych XPath/CSS

🕐 **BLOK 1 (45 min)** — Locators teoria
- Materiał: [Playwright locators docs](https://playwright.dev/python/docs/locators)
- Zadanie: Przeczytaj o wszystkich typach locatorów: get_by_role, get_by_text, get_by_label, get_by_placeholder, get_by_test_id

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Praktyka na saucedemo.com
- Materiał: [saucedemo.com](https://www.saucedemo.com) (demo app, darmowa)
- Zadanie: Znajdź 10 elementów na saucedemo.com używając TYLKO role/text/label locatorów (bez XPath/CSS)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz dlaczego get_by_role jest lepszy od `//button[@class='login']`?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Napisałem 10 locatorów używając tylko Playwright-recommended selectors

---

### Dzień 24 — Asercje — expect() API
> 📌 *Web-first assertions — asercje które czekają na warunek zamiast rzucać błąd natychmiast*

**🎯 Cel bloku**: Używasz expect(locator) API ze wszystkimi kluczowymi matchers

🕐 **BLOK 1 (45 min)** — Assertions API
- Materiał: [Playwright test assertions docs](https://playwright.dev/python/docs/test-assertions)
- Zadanie: Przetestuj wszystkie kluczowe: to_be_visible(), to_have_text(), to_have_value(), to_be_enabled(), to_have_url()

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Testy z asercjami na saucedemo
- Materiał: [saucedemo.com](https://www.saucedemo.com)
- Zadanie: Napisz 8 testów używając expect() API — każdy test musi mieć minimum 2 asercje

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: dlaczego `expect(locator).to_be_visible()` jest lepsze od `assert locator.is_visible()`?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 8 testów z expect() API, rozumiem auto-retry mechanizm

---

### Dzień 25 — Page Object Model w Python
> 📌 *POM pattern — separacja lokatorów od logiki testów*

**🎯 Cel bloku**: Projekt z POM — strony jako klasy Python, testy nie zawierają lokatorów

🕐 **BLOK 1 (45 min)** — POM teoria i implementacja
- Materiał: [Playwright POM docs](https://playwright.dev/python/docs/pom)
- Zadanie: Stwórz klasę `LoginPage` z metodami `goto()`, `login(user, password)`, `get_error_message()`

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Rozbudowanie POM
- Materiał: [saucedemo.com](https://www.saucedemo.com)
- Zadanie: Dodaj `InventoryPage`, `CartPage` — przepisz istniejące testy by używały Page Objects

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy testy są czytelne i nie zawierają żadnych lokatorów?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] POM zaimplementowany: LoginPage, InventoryPage, CartPage

---

### Dzień 26 — Fixtures + pytest-playwright
> 📌 *Integracja Playwright z pytest — page fixture, browser_context, reuse between tests*

**🎯 Cel bloku**: pytest-playwright zainstalowany, używasz page fixture zamiast ręcznego zarządzania przeglądarką

🕐 **BLOK 1 (45 min)** — pytest-playwright
- Materiał: [Playwright pytest integration docs](https://playwright.dev/python/docs/test-runners)
- Zadanie: `pip install pytest-playwright`, przepisz testy by używały `page` fixture zamiast `sync_playwright()`

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Konfiguracja fixtures
- Materiał: Dokumentacja pytest-playwright
- Zadanie: Skonfiguruj `browser_context_args` (viewport, base_url, locale) w conftest.py

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy testy uruchamiają się z `pytest` bez dodatkowych argumentów?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] pytest-playwright skonfigurowany, page fixture działa

---

### Dzień 27 — Interakcje z Formularzami
> 📌 *fill, click, select_option, file_chooser, dialogs — pełna obsługa UI*

**🎯 Cel bloku**: Obsługujesz wszystkie typy interakcji z elementami formularzy

�� **BLOK 1 (45 min)** — Interakcje teoria
- Materiał: [Playwright input docs](https://playwright.dev/python/docs/input)
- Zadanie: Przeczytaj dokumentację fill, type, click, select_option, check/uncheck, file chooser

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Obsługa dialogów i plików
- Materiał: [Playwright dialogs docs](https://playwright.dev/python/docs/dialogs)
- Zadanie: Napisz testy: formularz z checkboxami, select dropdown, alert dialog, upload pliku (https://the-internet.herokuapp.com/upload)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy obsługujesz dialogi (alert/confirm) w testach Playwright?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Obsługuję formularze, dialogi, uploady plików w Playwright

---

### Dzień 28 — Review + 10 Testów na saucedemo.com
> 📌 *Konsolidacja tygodnia 4 — kompletne testy logowania i koszyka*

**🎯 Cel bloku**: 10 testów pokrywających główne scenariusze saucedemo.com

🕐 **BLOK 1 (45 min)** — Planowanie i testy logowania
- Materiał: [saucedemo.com](https://www.saucedemo.com)
- Zadanie: Napisz 5 testów logowania: valid login, locked user, wrong password, empty fields, remember state

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Testy koszyka i produktów
- Materiał: [saucedemo.com](https://www.saucedemo.com)
- Zadanie: Napisz 5 testów produktów/koszyka: sortowanie, dodanie do koszyka, usunięcie, checkout flow

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy wszystkie 10 testów przechodzi i używają POM + fixtures?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 10 testów saucedemo.com — wszystkie passing ✅

---

## 📅 TYDZIEŃ 5 — Playwright Python Advanced

### Dzień 29 — Waits + Network Intercept
> 📌 *Auto-waiting Playwright i przechwytywanie żądań sieciowych*

**🎯 Cel bloku**: Rozumiesz auto-waiting, używasz page.route() do mockowania API

🕐 **BLOK 1 (45 min)** — Auto-waiting i actionability
- Materiał: [Playwright actionability docs](https://playwright.dev/python/docs/actionability)
- Zadanie: Przeczytaj o auto-waiting, napisz test z `page.wait_for_response()` i `page.wait_for_load_state()`

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Network intercept
- Materiał: [Playwright network docs](https://playwright.dev/python/docs/network)
- Zadanie: Napisz test używający `page.route()` do mockowania odpowiedzi API, zweryfikuj zachowanie UI

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz dlaczego Playwright nie potrzebuje `time.sleep()`?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Napisałem test z network intercept (page.route)

---

### Dzień 30 — API Testing z Playwright Request Context
> 📌 *Testowanie API bezpośrednio z Playwright — bez requests library*

**🎯 Cel bloku**: Piszesz testy API używając Playwright `APIRequestContext`

🕐 **BLOK 1 (45 min)** — API testing teoria
- Materiał: [Playwright API testing docs](https://playwright.dev/python/docs/api-testing)
- Zadanie: Przeczytaj docs, napisz 3 testy API dla https://reqres.in (GET users, POST create user, DELETE user)

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Hybrid tests (API + UI)
- Materiał: Playwright docs
- Zadanie: Napisz test który: (1) tworzy użytkownika przez API, (2) weryfikuje go przez UI

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz kiedy używać Playwright API vs requests library?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 3 testy API z Playwright request context + 1 hybrid test

---

### Dzień 31 — Screenshots, Trace Viewer, Allure
> 📌 *Debugowanie i raportowanie — trace viewer to killer feature Playwright*

**🎯 Cel bloku**: Trace viewer skonfigurowany, Allure raport z załączonymi screenshots

🕐 **BLOK 1 (45 min)** — Trace viewer i screenshots
- Materiał: [Playwright trace viewer docs](https://playwright.dev/python/docs/trace-viewer)
- Zadanie: Skonfiguruj trace w conftest.py (on_first_retry), otwórz trace dla failed testu

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Allure integracja
- Materiał: [allure-pytest docs](https://allurereport.org/docs/pytest/)
- Zadanie: Dodaj automatyczne screenshots w Allure dla failed testów, skonfiguruj video recording

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy trace viewer pokazuje wszystkie akcje, screenshoty i network calls?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Trace viewer działa, Allure pokazuje screenshots dla failed testów

---

### Dzień 32 — GitHub Actions CI
> 📌 *Continuous Integration — testy uruchamiają się automatycznie przy każdym pushu*

**🎯 Cel bloku**: Workflow GitHub Actions uruchamia testy Playwright na każdy push

🕐 **BLOK 1 (45 min)** — GitHub Actions basics
- Materiał: [Playwright CI docs](https://playwright.dev/python/docs/ci-intro)
- Zadanie: Stwórz `.github/workflows/playwright.yml` — instalacja zależności, playwright install, pytest

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Artefakty i optymalizacja
- Materiał: [GitHub Actions docs](https://docs.github.com/en/actions) (artifacts, caching)
- Zadanie: Dodaj upload Allure report jako artifact, dodaj cache dla pip i playwright browsers

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy CI jest zielone (✅) na GitHub Actions?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] GitHub Actions workflow passing ✅, artefakty uploadowane

---

### Dzień 33 — Visual Regression Basics
> 📌 *Testy wizualne — wykrywanie niezamierzonych zmian wyglądu UI*

**🎯 Cel bloku**: Napisałeś 3 testy visual regression z page.screenshot()

🕐 **BLOK 1 (45 min)** — Screenshot comparison teoria
- Materiał: [Playwright screenshots docs](https://playwright.dev/python/docs/screenshots) + [visual comparisons](https://playwright.dev/python/docs/test-snapshots)
- Zadanie: Napisz 3 testy porównujące screenshoty: `expect(page).to_have_screenshot()`

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Konfiguracja threshold
- Materiał: Playwright docs (snapshot comparison options)
- Zadanie: Skonfiguruj tolerancję różnic (threshold, maxDiffPixels), zaktualizuj snapshots po zmianie UI

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy potrafisz zaktualizować snapshots gdy UI się zmieni?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 3 visual regression tests działają i są w CI

---

### Dzień 34 — Praktyka — 15 UI + 10 API Testów
> 📌 *Intensywna sesja kodowania — budowanie fundamentu portfolio*

**🎯 Cel bloku**: 15 testów UI dla saucedemo.com + 10 testów API dla reqres.in

🕐 **BLOK 1 (45 min)** — Testy UI
- Materiał: [saucedemo.com](https://www.saucedemo.com)
- Zadanie: Uzupełnij do 15 testów UI (login, products, cart, checkout complete flow)

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Testy API
- Materiał: [reqres.in](https://reqres.in) (free mock API)
- Zadanie: Napisz 10 testów API: GET list, GET single, POST create, PUT update, PATCH, DELETE, 404 handling

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy wszystkie testy przechodzą w CI?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 25 testów łącznie (15 UI + 10 API), wszystkie w CI ✅

---

### Dzień 35 — Review Tygodnie 4–5 + Push na GitHub
> 📌 *Finalizacja bloku Playwright — przegląd i publikacja*

**🎯 Cel bloku**: Projekt Playwright gotowy na GitHub z pełnym README

🕐 **BLOK 1 (45 min)** — Code review własnego kodu
- Materiał: Twój projekt
- Zadanie: Przejrzyj cały kod: czy POM jest konsekwentny? Czy fixtures są właściwe? Czy CI jest zielone?

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — README i publikacja
- Materiał: Przykłady README z badges
- Zadanie: Napisz kompletny README z tech stack, instrukcją uruchomienia, badge CI, screen z Allure

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy projekt wygląda profesjonalnie na GitHub?
- [ ] Final commit i push
- [ ] Checkpoint: - [ ] Projekt Playwright Python opublikowany na GitHub z kompletnym README

---

## 🌐 TYGODNIE 6–7: REST API Advanced + Postman (Dni 36–49)

### Dzień 36 — requests Library Deep Dive
> 📌 *Zaawansowane użycie biblioteki requests — sessions, auth, headers, retry*

**🎯 Cel bloku**: Używasz requests.Session, obsługujesz auth, timeouts i retry logic

🕐 **BLOK 1 (45 min)** — requests zaawansowane
- Materiał: [requests docs](https://requests.readthedocs.io/en/latest/)
- Zadanie: Naucz się: Session objects, authentication (Basic, Bearer, API Key), custom headers, timeouts

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Retry i error handling
- Materiał: [requests docs — adapters](https://requests.readthedocs.io/en/latest/user/advanced/)
- Zadanie: Zaimplementuj HTTPAdapter z Retry policy, napisz test weryfikujący retry zachowanie

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz różnicę requests.get() vs requests.Session().get()?
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Używam Session, obsługuję auth i timeout w requests

---

### Dzień 37 — pytest + requests Fixtures
> 📌 *Integracja requests z pytest — reużywalne klienty API jako fixtures*

**🎯 Cel bloku**: API client jako pytest fixture z session scope

🕐 **BLOK 1 (45 min)** — API client fixture
- Materiał: Twój projekt + pytest docs
- Zadanie: Stwórz `api_client` fixture (scope=session) wrappujący requests.Session z base_url i auth

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Response validation patterns
- Materiał: [reqres.in](https://reqres.in)
- Zadanie: Napisz 5 testów API używając api_client fixture, każdy z pełną walidacją response (status, body, headers, timing)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] api_client fixture działa, 5 testów z pełną walidacją response

---

### Dzień 38 — JSON Schema Validation
> 📌 *Walidacja struktury odpowiedzi API — kontrakty API*

**🎯 Cel bloku**: Walidacja odpowiedzi API przy użyciu JSON Schema

🕐 **BLOK 1 (45 min)** — JSON Schema teoria
- Materiał: [jsonschema docs](https://python-jsonschema.readthedocs.io/en/stable/)
- Zadanie: `pip install jsonschema`, naucz się: type, properties, required, additionalProperties, pattern

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Schema validation w testach
- Materiał: [reqres.in](https://reqres.in)
- Zadanie: Napisz JSON Schema dla 3 endpoints reqres.in, zintegruj walidację w testach pytest

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] JSON Schema validation dla 3 endpoints reqres.in

---

### Dzień 39 — responses Library (Mocking)
> 📌 *Mockowanie HTTP responses w testach — testy bez zależności od zewnętrznych API*

**🎯 Cel bloku**: Używasz responses library do mockowania API w testach jednostkowych

🕐 **BLOK 1 (45 min)** — responses library
- Materiał: [responses library GitHub](https://github.com/getsentry/responses)
- Zadanie: `pip install responses`, napisz 3 testy mockując odpowiedzi HTTP (success, 404, 500)

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Zaawansowane mockowanie
- Materiał: responses docs (callbacks, passthrough)
- Zadanie: Napisz test z dynamicznym callback mockiem i passthrough dla wybranych URL

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 3 testy z responses mocking, w tym error scenarios

---

### Dzień 40 — Postman — Collections, Variables, Environments
> 📌 *Postman jako narzędzie testowania API — collections i environments*

**🎯 Cel bloku**: Masz kolekcję Postman dla reqres.in z environment variables

🕐 **BLOK 1 (45 min)** — Postman podstawy
- Materiał: [Postman Learning Center](https://learning.postman.com/docs/getting-started/overview/)
- Zadanie: Utwórz Collection dla reqres.in, skonfiguruj Environment z `base_url` i `token` variables

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Pre-request scripts i test scripts
- Materiał: [Postman test scripts docs](https://learning.postman.com/docs/tests-and-scripts/write-scripts/test-scripts/)
- Zadanie: Dodaj Pre-request scripts (generowanie tokenu) i test scripts (pm.test asercje) do 5 requestów

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Checkpoint: - [ ] Collection reqres.in gotowa z env variables i test scripts

---

### Dzień 41 — Newman CLI
> 📌 *Newman — uruchamianie kolekcji Postman z linii poleceń i w CI*

**🎯 Cel bloku**: Newman uruchamia kolekcję Postman z CLI i generuje raport HTML

🕐 **BLOK 1 (45 min)** — Newman install i użycie
- Materiał: [Newman npm](https://www.npmjs.com/package/newman)
- Zadanie: `npm install -g newman newman-reporter-htmlextra`, uruchom kolekcję z CLI

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Newman w GitHub Actions
- Materiał: GitHub Actions docs
- Zadanie: Dodaj Newman do istniejącego workflow GitHub Actions, publikuj HTML raport jako artifact

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Checkpoint: - [ ] Newman uruchamia kolekcję w CI, HTML raport generuje się automatycznie

---

### Dzień 42–43 — Pełny API Test Framework
> 📌 *Architektura projektu API tests — base client, config, fixtures, data*

**🎯 Cel bloku**: Profesjonalna struktura projektu API tests na GitHub

🕐 **BLOK 1 (45 min)** — Architektura projektu
- Materiał: Własna implementacja + inspiracja z GitHub (szukaj "pytest api framework")
- Zadanie: Zaprojektuj strukturę: `api/client.py`, `api/endpoints/`, `tests/`, `fixtures/`, `schemas/`

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Implementacja base client
- Materiał: Twoja architektura
- Zadanie: Zaimplementuj BaseAPIClient z metodami get/post/put/delete, auto-logging, schema validation

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] BaseAPIClient zaimplementowany z logging i schema validation

---

### Dzień 44–45 — Auth Testing + GitHub Actions dla API
> 📌 *Testowanie autoryzacji i CI dla API testów*

**🎯 Cel bloku**: Testy auth (Bearer token, API key) + CI passing

🕐 **BLOK 1 (45 min)** — Auth testing patterns
- Materiał: [reqres.in](https://reqres.in) + [httpbin.org](https://httpbin.org) (darmowy, brak wymagań)
- Zadanie: Napisz 5 testów auth: poprawny token, wygasły token, brak tokenu, zły format, API key

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — CI konfiguracja
- Materiał: GitHub Actions
- Zadanie: Skonfiguruj GitHub Actions dla API testów: secrets dla credentials, matrix testing (staging/prod)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] CI passing dla API tests z auth scenarios ✅

---

### Dzień 46–49 — Pełna Suite API + README
> 📌 *Finalizacja modułu REST API — kompletna suite testów + dokumentacja*

**🎯 Cel bloku**: Pełna suite API dla reqres.in (wszystkie endpointy) + README

- [ ] Zaimplementuj testy dla WSZYSTKICH endpoints reqres.in (GET, POST, PUT, PATCH, DELETE)
- [ ] Walidacja: status code, response body schema, response time < 2s
- [ ] Error scenarios: 404, 422 validation error, 500 handling
- [ ] README z instrukcją uruchomienia i opisem pokrycia
- [ ] CI passing ✅

---

## 🐳 TYGODNIE 8–9: Docker Basics

> Zasoby: [Docker Getting Started](https://docs.docker.com/get-started/) | [Docker Compose](https://docs.docker.com/compose/)  
> YouTube: ["Docker Tutorial for Beginners" — TechWorld with Nana](https://www.youtube.com/watch?v=3c-iBn73dDE) (bezpłatny, 3h)

### Koncepty Dockera
- [ ] Docker concepts: images, containers, layers, registries
- [ ] Dockerfile: FROM, COPY, RUN, CMD, WORKDIR, ENV
- [ ] Komendy: `docker run`, `docker build`, `docker ps`, `docker logs`, `docker exec`
- [ ] `docker-compose.yml`: services, volumes, networks, depends_on

### Docker w Testowaniu
- [ ] Napisz Dockerfile dla projektu pytest (python:3.12-slim base image)
- [ ] `docker-compose.yml`: services: tests + postgres (dla SQL testów)
- [ ] Uruchom pytest tests wewnątrz Docker container: `docker-compose up --exit-code-from tests`
- [ ] Selenium Grid w Docker: hub + chrome node (oficjalny obraz selenium/hub)
- [ ] GitHub Actions + Docker: cache layers (`actions/cache` dla Docker layers)

---

## 🏆 TYGODNIE 10–12: PORTFOLIO #1 + Aktywna Rekrutacja

### Specyfikacja Portfolio #1

**Nazwa repo**: `qa-automation-portfolio` (public GitHub)  
**Aplikacje testowane**: https://saucedemo.com (E2E UI) + https://reqres.in (API)  
**Stack technologiczny**:
- Python + pytest + Playwright + requests
- Docker + docker-compose
- GitHub Actions + Allure Report

**Minimalne wymagania**:
- 25 testów (15 UI + 10 API)
- Pełna struktura POM
- conftest.py z fixtures i markers
- CI: GitHub Actions uruchamia na każdy push, publikuje Allure jako artifact

---

### Tydzień 10 — Fundament Projektu

- [ ] Repo `qa-automation-portfolio` stworzony (public)
- [ ] README.md ze strukturą i planem
- [ ] Struktura projektu: `tests/`, `pages/`, `fixtures/`, `conftest.py`, `requirements.txt`
- [ ] 15 UI testów (login, products, cart, checkout)
- [ ] Allure report skonfigurowany i generuje się lokalnie

### Tydzień 11 — Kompletny Stack

- [ ] 10 API testów dla reqres.in
- [ ] Dockerfile + docker-compose.yml — testy uruchamiają się w kontenerze
- [ ] GitHub Actions: `.github/workflows/playwright.yml` — passing ✅
- [ ] Allure Report publikowany jako GitHub Actions artifact

### Tydzień 12 — Szlify i Rekrutacja

- [ ] README: tech stack badges (Python, Playwright, Docker, GitHub Actions), screenshot raportu Allure, instrukcja setup
- [ ] Post na LinkedIn z linkiem do projektu
- [ ] **Wyślij CV z linkiem do projektu na 20 ofert** (JustJoin, NoFluffJobs, BulldogJob, CJE)
- [ ] Tabela śledzenia rekrutacji: firma | data | status | technologie pytane
- [ ] Minimum 3 rozmowy telefoniczne umówione

---

## 💰 Projekcja po Miesiącach 2–3

```
🎯 TERAZ  — Python + pytest + Playwright + Docker + GitHub Actions + REST API
            B2B: 90–100 PLN/h ≈ 14 400–16 000 PLN netto
            UoP: 14 000–18 000 PLN brutto (Senior QA)
🏆 PORTFOLIO — publiczny projekt na GitHub = twarde dowody umiejętności
```

> ➡️ Następny plik: [qa_plan_03_pol_roku.md](qa_plan_03_pol_roku.md) — TypeScript + BDD + Cel 10k netto
