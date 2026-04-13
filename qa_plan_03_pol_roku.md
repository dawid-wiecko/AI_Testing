# 📅 Miesiące 4–6 — TypeScript + BDD + Cel 10 000 PLN netto

> **Cel**: Drugi golden stack (TypeScript+Playwright), BDD/Gherkin, Portfolio #2, osiągnąć 10 000 PLN netto  
> **Rezultat**: Dwa kompletne stosy technologiczne + BDD = góra najlepiej płatnych ofert QA w Polsce

---

## 🔷 TYGODNIE 13–15: TypeScript + Playwright TypeScript

> Znasz już Playwright API (z Pythona) — nauka wersji TypeScript jest **2× szybsza**.  
> Po 3 tygodniach masz **DWA golden stacks**: Python i TypeScript.

---

### 📅 TYDZIEŃ 13 — TypeScript Fundamentals (fast track dla Python devów)

### Dzień 57 (Tydzień 13, Dzień 1) — Typy Podstawowe
> 📌 *TypeScript dla programistów Python — system typów*

**🎯 Cel bloku**: Rozumiesz typy TS i piszesz kod z adnotacjami typów

🕐 **BLOK 1 (45 min)** — Podstawy TypeScript
- Materiał: [TypeScript Basic Types](https://www.typescriptlang.org/docs/handbook/2/basic-types.html)
- Zadanie: W [TS Playground](https://www.typescriptlang.org/play/) napisz 10 przykładów: string, number, boolean, array, tuple, Type Aliases

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Type Aliases i porównanie z Python
- Materiał: [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/)
- Zadanie: Dla każdego typu TS napisz ekwiwalent Python — zrozum różnice filozoficzne między językami

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz różnicę `type` vs wartość w TypeScript?
- [ ] Checkpoint: - [ ] Napisałem 10 przykładów typów TS w Playground

---

### Dzień 58 — Interfaces, Union Types, Optional Properties
> 📌 *Struktury danych w TypeScript — jak opisywać kształt obiektów*

**🎯 Cel bloku**: Tworzysz interfaces z optional properties, używasz union types

🕐 **BLOK 1 (45 min)** — Interfaces i objects
- Materiał: [TypeScript Objects](https://www.typescriptlang.org/docs/handbook/2/objects.html)
- Zadanie: Napisz interfaces dla: User, Product, APIResponse — z optional i required properties

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Union types i type narrowing
- Materiał: [TypeScript Union Types](https://www.typescriptlang.org/docs/handbook/2/narrowing.html)
- Zadanie: Napisz 5 funkcji używających union types i type guards (typeof, instanceof, in)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy potrafisz napisać interface i użyć go jako typ parametru funkcji?
- [ ] Checkpoint: - [ ] Interfaces z optional properties, union types — napisane i działające

---

### Dzień 59 — Generics, Enums, Classes
> 📌 *OOP w TypeScript — klasy i typy generyczne*

**🎯 Cel bloku**: Piszesz klasy TS z access modifiers, enums i generics

🕐 **BLOK 1 (45 min)** — Classes i modifiers
- Materiał: [TypeScript Classes](https://www.typescriptlang.org/docs/handbook/2/classes.html)
- Zadanie: Napisz klasę `APIClient<T>` z generic response type, public/private/protected methods

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Enums i praktyczne generics
- Materiał: [TypeScript Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html)
- Zadanie: Napisz enum dla HTTP methods, generic function `fetchData<T>(url: string): Promise<T>`

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz czym jest `T` w `class Container<T>`?
- [ ] Checkpoint: - [ ] Klasy z access modifiers, enums, generics — działające przykłady

---

### Dzień 60 — Async/Await w TypeScript
> 📌 *Asynchroniczność w TS — kluczowe dla Playwright (który jest async)*

**🎯 Cel bloku**: Rozumiesz Promises i async/await w TypeScript

🕐 **BLOK 1 (45 min)** — Async/await i modules
- Materiał: [TypeScript Handbook — modules](https://www.typescriptlang.org/docs/handbook/)
- Zadanie: Napisz 3 async funkcje: fetch danych, retry logic, parallel requests z Promise.all

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — tsconfig.json i imports
- Materiał: [tsconfig reference](https://www.typescriptlang.org/tsconfig)
- Zadanie: Skonfiguruj tsconfig.json dla projektu testowego (strict: true, ES2022, esModuleInterop)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz różnicę `async function` vs `function` zwracające Promise?
- [ ] Checkpoint: - [ ] async/await działa, tsconfig.json skonfigurowany

---

### Dzień 61 — Node.js + npm Basics
> 📌 *Ekosystem Node.js — package.json, scripts, node_modules*

**🎯 Cel bloku**: Rozumiesz ekosystem npm i konfigurujesz projekt Node.js

🕐 **BLOK 1 (45 min)** — Node.js i npm
- Materiał: [Node.js Introduction](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs)
- Zadanie: Stwórz projekt npm: `npm init -y`, zainstaluj TypeScript, skonfiguruj scripts w package.json

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — TypeScript compilation
- Materiał: [TypeScript docs](https://www.typescriptlang.org/docs/)
- Zadanie: Skompiluj swój kod TS do JS, uruchom przez Node.js, zrozum process kompilacji

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Sprawdź: czy rozumiesz relację między TS a JS?
- [ ] Checkpoint: - [ ] Projekt npm z TypeScript kompiluje się i uruchamia

---

### Dzień 62 — TypeScript Exercises
> 📌 *Ćwiczenia TypeScript — utrwalenie wiedzy przez rozwiązywanie problemów*

**🎯 Cel bloku**: Rozwiązałeś 8 ćwiczeń TypeScript Exercises

🕐 **BLOK 1 (45 min)** — Exercises 1–4
- Materiał: [TypeScript Exercises](https://typescript-exercises.github.io/) (exercises 1–4)
- Zadanie: Rozwiąż ćwiczenia 1–4 bez podpowiedzi

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Exercises 5–8
- Materiał: [TypeScript Exercises](https://typescript-exercises.github.io/) (exercises 5–8)
- Zadanie: Rozwiąż ćwiczenia 5–8 — jeśli utkniesz, sprawdź hints po 15 min

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Checkpoint: - [ ] 8 TypeScript Exercises rozwiązanych

---

### Dzień 63 — Review TypeScript + Przepisanie Python na TS
> 📌 *Konsolidacja — przekład kodu Python do TypeScript*

**🎯 Cel bloku**: Rozumiesz różnice Python↔TypeScript i potrafisz "myśleć w TS"

🕐 **BLOK 1 (45 min)** — Przepisanie funkcji Python
- Materiał: Twój kod Python
- Zadanie: Przepisz 5 funkcji Python (z fixtures, helper functions) na TypeScript

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Porównanie i retrospekcja
- Materiał: Twój kod Python i TypeScript
- Zadanie: Napisz krótki dokument porównujący: co jest łatwiejsze w Python, co w TypeScript, gdzie TS wygrywa

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Checkpoint: - [ ] 5 funkcji Python przepisanych na TS, dokument porównawczy napisany

---

## 📅 TYDZIEŃ 14 — Playwright TypeScript — Setup i Fundamenty

### Dzień 64 — Inicjalizacja Projektu Playwright TS
> 📌 *npm init playwright@latest — oficjalny generator projektu*

**🎯 Cel bloku**: Projekt Playwright TypeScript zainicjalizowany i pierwsza test passing

🕐 **BLOK 1 (45 min)** — Setup projektu
- Materiał: [Playwright TypeScript docs](https://playwright.dev/docs/intro)
- Zadanie: `npm init playwright@latest`, skonfiguruj playwright.config.ts (baseURL, workers, reporter)

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Pierwsze testy TS
- Materiał: [Playwright docs](https://playwright.dev/docs/)
- Zadanie: Napisz 5 testów na https://automationexercise.com — zrozum składnię TS vs Python

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Projekt Playwright TS działa, 5 testów passing ✅

---

### Dzień 65 — Page Objects w TypeScript
> 📌 *POM pattern w TypeScript — klasy z typed methods*

**🎯 Cel bloku**: Page Objects z TypeScript — typed locators, typed methods, typed return values

🕐 **BLOK 1 (45 min)** — Page Objects TS
- Materiał: [Playwright POM docs](https://playwright.dev/docs/pom)
- Zadanie: Stwórz `HomePage` class z TypeScript — constructor(page: Page), typed methods

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Rozbudowanie POM
- Materiał: [automationexercise.com](https://automationexercise.com)
- Zadanie: Stwórz 3 Page Objects: HomePage, LoginPage, ProductsPage — z typed methods i return types

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 3 typed Page Objects, testy używają POM bez bezpośrednich locatorów

---

### Dzień 66 — Fixtures w TypeScript: test.extend()
> 📌 *Fixtures w Playwright TS — test.extend() pattern*

**🎯 Cel bloku**: Custom fixtures z test.extend() — typed fixtures

🕐 **BLOK 1 (45 min)** — test.extend() pattern
- Materiał: [Playwright fixtures docs](https://playwright.dev/docs/test-fixtures)
- Zadanie: Utwórz custom fixtures: `loggedInPage`, `authenticatedContext` używając test.extend()

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Fixtures z Page Objects
- Materiał: Playwright docs
- Zadanie: Połącz fixtures z Page Objects: fixture zwracający `LoginPage`, `ProductsPage` instancje

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] test.extend() fixtures z Page Objects działają

---

### Dzień 67 — API Testing w TypeScript
> 📌 *request fixture w Playwright TS — testy API z TypeScript*

**🎯 Cel bloku**: 5 testów API w TypeScript z typed response interfaces

🕐 **BLOK 1 (45 min)** — request fixture
- Materiał: [Playwright API testing docs](https://playwright.dev/docs/api-testing)
- Zadanie: Napisz 5 testów API dla reqres.in używając `request` fixture z TypeScript

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Typed API responses
- Materiał: Własna implementacja
- Zadanie: Stwórz interfaces dla API responses reqres.in, użyj ich w testach (response.json() as UserResponse)

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 5 typed API testów w TypeScript

---

### Dzień 68 — Parallel Execution + GitHub Actions TS
> 📌 *Zrównoleglenie testów — konfiguracja workers i CI dla projektu TS*

**🎯 Cel bloku**: Testy uruchamiają się równolegle w CI, GitHub Actions passing

🕐 **BLOK 1 (45 min)** — Parallel configuration
- Materiał: [Playwright parallelism docs](https://playwright.dev/docs/test-parallel)
- Zadanie: Skonfiguruj workers: 4 lokalnie, 2 w CI; dodaj fullyParallel: true do playwright.config.ts

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — GitHub Actions TS
- Materiał: [Playwright CI docs](https://playwright.dev/docs/ci-intro)
- Zadanie: Stwórz `.github/workflows/playwright-ts.yml` — passing ✅

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] CI passing ✅, testy uruchamiają się równolegle

---

## 📅 TYDZIEŃ 15 — Playwright TS Advanced + 15 Testów

### Dzień 69–77 — 15 Testów na automationexercise.com

Każdy dzień: Blok 1 (45 min) + Przerwa + Blok 2 (45 min) + Podsumowanie

**Aplikacja**: [automationexercise.com](https://automationexercise.com) (darmowa, bogata w funkcje)  
**Zasoby**: [Playwright docs](https://playwright.dev/docs/)

- [ ] Testy rejestracji i logowania (3 testy + edge cases)
- [ ] Testy wyszukiwania produktów (2 testy + parametrize)
- [ ] Testy koszyka (3 testy — add, remove, update quantity)
- [ ] Testy checkout flow (3 testy — full flow, validation, payment)
- [ ] Testy kontaktu (2 testy — form submission)
- [ ] Visual regression — 2 kluczowe strony
- [ ] GitHub Actions — wszystkie passing ✅

---

## 🥒 TYGODNIE 16–17: BDD + Gherkin

### Dzień 78 — Gherkin Syntax
> 📌 *Gherkin — język biznesowy do opisywania testów*

**🎯 Cel bloku**: Piszesz scenariusze Gherkin które rozumie zarówno biznes jak i deweloperzy

🕐 **BLOK 1 (45 min)** — Gherkin fundamenty
- Materiał: [Cucumber Gherkin docs](https://cucumber.io/docs/gherkin/)
- Zadanie: Przeczytaj całą dokumentację Gherkin, napisz 3 Feature files ręcznie (nie implementuj jeszcze)

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Feature files dla saucedemo
- Materiał: [saucedemo.com](https://www.saucedemo.com)
- Zadanie: Napisz 5 Gherkin scenarios dla saucedemo.com: login, add to cart, checkout, logout, sort products

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Checkpoint: - [ ] 5 Feature files napisanych w poprawnym Gherkin

---

### Dzień 79 — pytest-bdd — Step Definitions
> 📌 *Implementacja kroków BDD w Python — łączenie Gherkin z kodem*

**🎯 Cel bloku**: Step definitions zaimplementowane dla 3 scenariuszy

🕐 **BLOK 1 (45 min)** — pytest-bdd setup
- Materiał: [pytest-bdd docs](https://pytest-bdd.readthedocs.io/en/stable/)
- Zadanie: `pip install pytest-bdd`, zaimplementuj step definitions dla najprostszego scenariusza logowania

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Rozbudowanie steps
- Materiał: pytest-bdd docs
- Zadanie: Zaimplementuj step definitions dla wszystkich 5 scenariuszy — używając Page Objects z Playwright

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] 5 scenariuszy BDD z działającymi step definitions

---

### Dzień 80 — Scenario Outline + Examples
> 📌 *Parametryzacja w BDD — jeden scenariusz, wiele danych*

**🎯 Cel bloku**: Scenario Outline z Examples table — parametryzacja BDD testów

🕐 **BLOK 1 (45 min)** — Scenario Outline teoria
- Materiał: [Cucumber Scenario Outline docs](https://cucumber.io/docs/gherkin/reference/#scenario-outline)
- Zadanie: Przepisz scenariusz logowania jako Scenario Outline z 3 zestawami danych

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Implementacja
- Materiał: pytest-bdd docs
- Zadanie: Zaimplementuj Scenario Outline z Examples — upewnij się że parametry przepływają przez step definitions

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] Scenario Outline z 3 zestawami danych działa

---

### Dzień 81 — Behave Framework (alternatywa)
> 📌 *Behave — alternatywny framework BDD dla Python*

**🎯 Cel bloku**: Rozumiesz kiedy używać pytest-bdd vs Behave

🕐 **BLOK 1 (45 min)** — Behave basics
- Materiał: [Behave docs](https://behave.readthedocs.io/en/stable/)
- Zadanie: `pip install behave`, przepisz 1 scenariusz z pytest-bdd na Behave — porównaj składnię

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Porównanie i decyzja
- Materiał: Własna analiza
- Zadanie: Napisz dokument "pytest-bdd vs Behave" — kiedy używać którego w projektach komercyjnych

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Checkpoint: - [ ] Rozumiem różnice pytest-bdd vs Behave i kiedy wybrać który

---

### Dzień 82 — BDD + Playwright Integration
> 📌 *Połączenie BDD z Playwright — pełny stack BDD*

**🎯 Cel bloku**: Scenariusze BDD uruchamiane przez pytest + Playwright + Allure

🕐 **BLOK 1 (45 min)** — Integracja BDD + Playwright
- Materiał: Własna implementacja
- Zadanie: Połącz pytest-bdd z Playwright fixtures — step definitions używają `page` z pytest-playwright

☕ **PRZERWA (15 min)** — wstań, odejdź od ekranu

🕑 **BLOK 2 (45 min)** — Allure + BDD reports
- Materiał: [Allure pytest-bdd docs](https://allurereport.org/docs/pytest-bdd/)
- Zadanie: Skonfiguruj Allure dla pytest-bdd — Feature/Scenario/Step w raporcie

📝 **PODSUMOWANIE (15 min)**
- [ ] Napisz 3 nowe rzeczy których się nauczyłeś
- [ ] Commit na GitHub
- [ ] Checkpoint: - [ ] BDD + Playwright + Allure — pełny stack działa

---

### Dzień 83–84 — 8 BDD Scenariuszy dla saucedemo.com

Każdy dzień: pełny format z Blokami

- [ ] Feature: Login — 2 scenariusze (happy path, invalid credentials)
- [ ] Feature: Products — 2 scenariusze (sort, filter)
- [ ] Feature: Cart — 2 scenariusze (add, remove)
- [ ] Feature: Checkout — 2 scenariusze (complete, cancel)
- [ ] Allure raport pokazuje: Feature → Scenario → Step hierarchy
- [ ] GitHub Actions — BDD tests passing ✅

---

## 🚀 TYGODNIE 18–20: Portfolio #2 + Intensywna Rekrutacja

### Specyfikacja Portfolio #2

**Nazwa repo**: `playwright-ts-automation` (public GitHub)  
**Aplikacja**: [automationexercise.com](https://automationexercise.com) LUB [the-internet.herokuapp.com](https://the-internet.herokuapp.com)  
**Stack**: TypeScript + Playwright + API tests + BDD scenarios  
**CI**: GitHub Actions ✅

### Checklista Portfolio #2

- [ ] Repo stworzony, README kompletny z badges
- [ ] 20 testów UI (TypeScript + Playwright) — passing ✅
- [ ] 10 testów API z typed responses
- [ ] 5 scenariuszy BDD (Gherkin + pytest-bdd lub Playwright)
- [ ] GitHub Actions passing ✅
- [ ] CV zaktualizowane — dodano: TypeScript, Playwright TS, BDD, Docker
- [ ] Wysłano 30+ aplikacji w tygodniach 18–20
- [ ] Tabela śledzenia rekrutacji — aktywna

---

## 🔀 DECISION POINT — Koniec Miesiąca 6

> Czas wybrać specjalizację na miesiące 7–12. Wybierz na podstawie feedbacku z rozmów kwalifikacyjnych.

### Wskazówki decyzyjne

| Sygnał z rynku | Rekomendacja |
|----------------|-------------|
| Rekruterzy pytają o Java, Spring Boot, fintech | → TRACK A: Java Enterprise |
| Rekruterzy pytają o SQL, dbt, data pipelines | → TRACK B: Data QA |
| Brak wyraźnego sygnału | → TRACK A (szerszy rynek) |

### Track A: Java Enterprise
- [ ] **Wybrałem TRACK A** — Java Enterprise
- Stawki: 110–140 PLN/h B2B
- Firmy: fintech, banking, e-commerce enterprise
- Stack: Java + Selenium/REST Assured + JUnit 5 + Testcontainers

### Track B: Data QA
- [ ] **Wybrałem TRACK B** — Data QA
- Stawki: 110–150 PLN/h B2B
- Firmy: data engineering, analytics, cloud-first
- Stack: Python + SQL + dbt + pytest + Spark

---

## ✅ Podsumowanie Miesiące 4–6

- [ ] TypeScript fundamenty ukończone (TypeScript Exercises 1–8)
- [ ] Playwright TypeScript — 15+ testów na automationexercise.com
- [ ] BDD/Gherkin — 8 scenariuszy z step definitions
- [ ] Portfolio #2 opublikowany na GitHub
- [ ] 30+ aplikacji wysłanych w tygodniach 18–20
- [ ] Minimum 5 rozmów technicznych odbytych
- [ ] Decision Point — track wybrany

---

## 💰 Projekcja po Miesiącach 4–6

```
✅ TERAZ  — 2 golden stacks: Python+Playwright + TypeScript+Playwright
            + BDD + Docker + REST API + Portfolio #1 + Portfolio #2
            
B2B:   100–110 PLN/h ≈ 16 000–17 600 PLN netto
UoP:   17 000–22 000 PLN brutto (Senior QA Automation)

🎯 CEL 10 000 PLN NETTO — OSIĄGALNY TERAZ
   B2B 90 PLN/h × 168h × 0.81 = 12 247 PLN netto (bez kosztów)
   B2B 95 PLN/h × 168h × 0.81 = 12 927 PLN netto
```

> ➡️ Następny plik: [qa_plan_04_rok.md](qa_plan_04_rok.md) — Enterprise Stack + Job Security
