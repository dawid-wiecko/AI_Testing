# 📅 Miesiące 7–12 — Enterprise Stack + Job Security

> **Cel**: Java Enterprise LUB Data QA LUB C# QA (add-on), AWS basics, 110–130 PLN/h  
> **Format**: Miesięczny (mniej granularny niż wcześniejsze pliki — masz już nawyk nauki)

---

## 🔀 Wybierz Swój Track

> Wróć do Decision Point z końca miesiąca 6 i sprawdź który track wybrałeś.  
> **Dane rynkowe (kwiecień 2026)** pomagają wybrać:

| Track | Oferty MID PL | Stawka B2B MID | Twój match po nauce | Czas nauki |
|-------|:-------------:|:--------------:|:-------------------:|:----------:|
| **A: Java** | ~35–50 | 120–145 PLN/h | 70–80% | 4–5 mies. |
| **B: Data QA** | ~15–25 | 130–150 PLN/h | 60–70% | 4 mies. |
| **C: C# QA** | ~8–15 | 105–130 PLN/h | **90–95%** | **4–6 tyg.** |

> ⚠️ **Ważne**: Track C (C#) ma najmniej ofert, ale **Ty już znasz C#** — czas nauki to 4–6 tygodni,  
> nie 4–5 miesięcy. Rekomendacja: **Track A lub B jako główny + Track C jako add-on** (po 4–6 tyg.).  
> Firmy w Trójmieście: **Xopero Gdynia, HCLTech Gdańsk** aktywnie rekrutują C# QA lokalnie.

- [ ] **TRACK A: Java Enterprise** — fintech, banking, e-commerce enterprise (~35–50 ofert, najwyższy ceiling)
- [ ] **TRACK B: Data QA** — data engineering, analytics, cloud-first (~15–25 ofert, premium niche)
- [ ] **TRACK C: C# QA add-on** — .NET companies, Xopero/Veeam/HCLTech (~8–15 ofert, 4–6 tyg. bo C# już znasz)

---

## 🅲 TRACK C: C# QA Add-on (4–6 tygodni — równolegle z Track A lub po nim)

> **Dla kogo**: Jeśli po 6 miesiącach chcesz od razu aplikować do .NET firm lokalnie  
> (Xopero Gdynia, HCLTech Gdańsk) lub masz mało odpowiedzi na CV.

> **Dlaczego warto**: 75–80% match JUŻ TERAZ z obecnymi umiejętnościami. Po 4–6 tygodniach → 90–95%.  
> SpecFlow **NIE** jest wart nauki — pojawia się w dosłownie 2–5 ofertach w całej Polsce.  
> Zamiast tego: **NUnit + xUnit + Playwright C# + RestSharp**.

### Tydzień 1–2: NUnit + xUnit w QA kontekście

- [ ] NUnit — atrybuty: `[Test]`, `[SetUp]`, `[TearDown]`, `[TestCase]`, `[TestFixture]`
  - Materiał: [NUnit docs](https://docs.nunit.org/) (bezpłatny)
  - Porównanie z pytest: `[TestCase]` ≈ `@pytest.mark.parametrize`, `[SetUp]` ≈ fixture
- [ ] xUnit — `[Fact]`, `[Theory]`, `[InlineData]`, constructor injection (zamiast SetUp)
  - Materiał: [xUnit docs](https://xunit.net/docs/getting-started/netfx/visual-studio) (bezpłatny)
  - Uwaga: xUnit rośnie szybciej niż NUnit — preferowany w nowych projektach
- [ ] Uruchom 10 testów w każdym frameworku dla saucedemo.com
- [ ] Integracja z GitHub Actions: `.github/workflows/dotnet.yml`

### Tydzień 3–4: Playwright C# (.NET)

> Znasz już Playwright API z Pythona — nauka C# bindingu to kwestia składni, nie nowych konceptów.

- [ ] Instalacja: `dotnet new playwright` lub NuGet package
  - Materiał: [Playwright .NET docs](https://playwright.dev/dotnet/docs/intro) (bezpłatny)
- [ ] Przepisz 10 testów z Portfolio #1 (Python) na C# — porównaj API:
  ```csharp
  // Python: await page.get_by_role("button", name="Login").click()
  await page.GetByRole(AriaRole.Button, new() { Name = "Login" }).ClickAsync();
  // Python: await expect(page.locator(".error")).to_be_visible()
  await Expect(page.Locator(".error")).ToBeVisibleAsync();
  ```
- [ ] Page Object Model w C# — klasy z `IPage`, metody `async Task<T>`
- [ ] NUnit + Playwright integration (fixtures pattern w C#)
- [ ] GitHub Actions pipeline dla .NET + Playwright

### Tydzień 5–6: RestSharp (API testing C#) + Portfolio C# QA

- [ ] RestSharp basics — `RestClient`, `RestRequest`, `Execute<T>`
  - Materiał: [RestSharp docs](https://restsharp.dev/) (bezpłatny)
  - Porównanie z requests (Python): podobny pattern, inna składnia
- [ ] Serialize/deserialize JSON: `System.Text.Json` lub `Newtonsoft.Json`
- [ ] Napisz 10 API testów dla reqres.in z RestSharp + NUnit
- [ ] **Portfolio #3 C#** (jeśli Track C wybrany zamiast Java portfolio):
  - Repo: `qa-csharp-automation` (publiczny GitHub)
  - Tech: C# + Playwright + xUnit + RestSharp + GitHub Actions
  - 15 UI tests + 10 API tests
  - README z badges

#### Firmy do aplikowania po Track C
| Firma | Lokalizacja | Stack | Match |
|-------|-------------|-------|:-----:|
| **Xopero Software** | Gdynia 🏠 | C# + NUnit/xUnit + Selenium/Playwright | ~90% |
| **HCLTech** | Gdańsk 🏠 | Python/.NET/PowerShell (Airbus) | ~85% |
| **DCG** | Trójmiasto 🏠 | .NET + Playwright | ~88% |
| **Veeam Software** | Remote | C# + automation frameworks | ~80% |
| **Scalo** | Remote | C# + xUnit + REST API + GitLab CI | ~90% |

> 💰 **Stawki C# QA**: 105–130 PLN/h B2B (16 800–20 800 PLN netto) — nieznacznie poniżej Java,  
> ale **Xopero Gdynia płaci 60–85 PLN/h** (uwaga: to oferta lokalna UoP-style, negocjuj B2B!)

---

---

# 🅰️ TRACK A: Java Enterprise (Miesiące 7–12)

## Miesiąc 7–8 — Java Fundamentals dla Testerów

> **Zasoby**:
> - [ToolsQA Java Tutorial](https://toolsqa.com/java/java-tutorial/) (bezpłatny)
> - [W3Schools Java](https://www.w3schools.com/java/)
> - YouTube: ["Java for Beginners" — Bro Code](https://www.youtube.com/watch?v=xk4_1vDrzzo) (bezpłatny, 12h)

### Miesiąc 7 — Core Java

**Dziennie: 1 blok teorii (45 min) + 1 blok ćwiczeń (45 min) + podsumowanie (15 min)**

#### Tydzień 1–2: Podstawy języka
- [ ] Typy danych, zmienne, operatory, sterowanie przepływem (if/switch/for/while)
- [ ] Tablice, metody, rekurencja
- [ ] Kompilacja i uruchamianie: `javac` + `java`, IntelliJ IDEA Community (bezpłatny)
- [ ] HackerRank Java — pierwsze 10 zadań: [hackerrank.com/domains/java](https://www.hackerrank.com/domains/java)
- [ ] Porównanie z Python: co jest trudniejsze, co łatwiejsze, dlaczego Java wymaga typów

#### Tydzień 3–4: OOP
- [ ] Klasy i obiekty, konstruktory, `this`, `static`
- [ ] Dziedziczenie: `extends`, `super`, nadpisywanie metod
- [ ] Interfejsy: `implements`, default methods, functional interfaces
- [ ] Polimorfizm: upcasting/downcasting, `instanceof`
- [ ] Wyjątki: `try/catch/finally`, `throws`, własne klasy wyjątków
- [ ] Kolekcje: `ArrayList`, `HashMap`, `HashSet`, `LinkedList` — kiedy używać którego

#### Checklisty Miesiąc 7
- [ ] Typy danych, zmienne, operatory, sterowanie (if/for/while) — ✅
- [ ] OOP: klasy, dziedziczenie, interfejsy, polimorfizm — ✅
- [ ] Kolekcje: ArrayList, HashMap, HashSet — ✅
- [ ] Wyjątki: try/catch, własne exceptions — ✅
- [ ] 20 zadań Java na [HackerRank](https://www.hackerrank.com/domains/java) — ✅

### Miesiąc 8 — Maven + JUnit 5

**Zasoby**:
- [Maven Getting Started](https://maven.apache.org/guides/getting-started/) (bezpłatny)
- [JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/) (bezpłatny)

#### Tydzień 5–6: Maven
- [ ] `pom.xml`: dependencies, plugins, profiles, properties
- [ ] Build lifecycle: `clean`, `compile`, `test`, `package`, `install`
- [ ] Dodawanie dependencies: JUnit 5, AssertJ, Selenium, REST Assured
- [ ] Maven Surefire Plugin — raportowanie testów

#### Tydzień 7–8: JUnit 5
- [ ] Anotacje: `@Test`, `@BeforeEach`, `@AfterEach`, `@BeforeAll`, `@AfterAll`
- [ ] `@ParameterizedTest` — `@ValueSource`, `@CsvSource`, `@MethodSource`
- [ ] `@DisplayName`, `@Tag`, `@Disabled`, `@Nested`
- [ ] AssertJ assertions (bardziej czytelne niż JUnit assert): `assertThat(x).isEqualTo(y)`
- [ ] Testy wyjątków: `assertThrows(Exception.class, () -> ...)`

#### Checklisty Miesiąc 8
- [ ] Maven: pom.xml, dependencies, build lifecycle — ✅
- [ ] JUnit 5: @Test, @BeforeEach, @AfterAll, @ParameterizedTest — ✅
- [ ] AssertJ — 20 assertions używanych w testach — ✅
- [ ] IntelliJ IDEA — komfortowe środowisko pracy — ✅

---

## Miesiąc 9 — REST Assured + Advanced JUnit 5

> **Zasoby**:
> - [REST Assured official docs](https://rest-assured.io/)
> - [REST Assured Wiki — Usage](https://github.com/rest-assured/rest-assured/wiki/Usage) (bezpłatny)

### Tematy miesiąca
- REST Assured given/when/then DSL — czytelne testy API
- JsonPath i XmlPath — wyciąganie wartości z response
- Request specifications — reużywalne konfiguracje requests
- Serialization/deserialization — Java POJO ↔ JSON (Jackson/Gson)
- Auth: Basic, OAuth2, API Key w REST Assured
- Response validation: status code, body, headers, schema validation

### Checklisty Miesiąc 9
- [ ] REST Assured given/when/then — 10 testów API dla reqres.in — ✅
- [ ] JsonPath — wyciąganie wartości zagnieżdżonych — ✅
- [ ] Serialization z Jackson — POJO ↔ JSON — ✅
- [ ] GitHub Actions dla REST Assured projektu — ✅

---

## Miesiąc 10 — Selenium Java + TestNG

> **Zasoby**:
> - [Selenium official docs](https://www.selenium.dev/documentation/) (bezpłatny)
> - [TestNG docs](https://testng.org/doc/documentation-main.html) (bezpłatny)

### Tematy miesiąca
- WebDriverManager — automatyczne zarządzanie driverami (koniec ręcznego pobierania chromedriver)
- Page Object Model w Java — klasy stron, PageFactory, @FindBy
- TestNG anotacje: `@Test`, `@BeforeSuite`, `@DataProvider`, `@Listeners`
- TestNG XML suite files — grupowanie i sekwencjonowanie testów
- Parallel test execution z TestNG
- Selenium Grid — remote execution (Docker)

### Checklisty Miesiąc 10
- [ ] WebDriverManager zainstalowany, driver zarządzany automatycznie — ✅
- [ ] POM w Java — 3 Page Objects zaimplementowane — ✅
- [ ] 15 testów E2E z Selenium Java dla saucedemo.com — ✅
- [ ] Porównanie POM Java vs Python — co jest inne? — dokument napisany

---

## Miesiąc 11 — Testcontainers + Docker Advanced + Jenkins Pipeline

> **Zasoby**:
> - [Testcontainers docs](https://testcontainers.com/) (bezpłatny)
> - [Jenkins Pipeline docs](https://www.jenkins.io/doc/book/pipeline/) (bezpłatny)

### Testcontainers
- [ ] Koncepcja: testy integracyjne z prawdziwymi serwisami w Docker
- [ ] `@Testcontainers`, `@Container`, `PostgreSQLContainer`, `GenericContainer`
- [ ] Test suite uruchamiany z PostgreSQL w Testcontainers
- [ ] Porównanie: Testcontainers vs mock vs test DB

### Jenkins Pipeline
- [ ] Declarative Pipeline — składnia `Jenkinsfile`
- [ ] Stages: Build → Test → Report → Deploy
- [ ] `post { always { ... } }` — zawsze publikuj raport
- [ ] Jenkins + GitHub — webhook triggering
- [ ] Jenkinsfile napisany dla projektu Java

### Checklisty Miesiąc 11
- [ ] Test suite uruchamiany w Testcontainers (PostgreSQL + aplikacja) — ✅
- [ ] Jenkinsfile napisany — Build → Test → Report — ✅
- [ ] Jenkins lokalny (Docker) z pipeline dla projektu — ✅

---

## Miesiąc 12 — Portfolio #3 + Mock Interviews + Negocjacja Stawki

### Portfolio #3 — Java Enterprise

**Wymagania**:
- Java + REST Assured + Selenium/WebDriver + Docker + Testcontainers + GitHub Actions
- Minimum 20 testów (10 API + 10 UI)
- README z pełną dokumentacją

### Przygotowanie do Rozmów Kwalifikacyjnych

**Mock Interview Preparation**:
- [ ] [Top pytania QA Automation](https://www.interviewbit.com/automation-testing-interview-questions/) — przejdź listę i odpowiedz na każde
- [ ] Mock: SQL (EXPLAIN, JOIN edge cases, window functions) — odpowiedź bez notatek
- [ ] Mock: Playwright Python (fixtures, POM, API testing) — live coding
- [ ] Mock: Java (OOP basics, collections, JUnit 5) — whiteboard explanation
- [ ] Mock: CI/CD (GitHub Actions, Jenkins, Docker) — narysuj diagram pipeline

### Checklisty Miesiąc 12
- [ ] Portfolio #3 opublikowany na GitHub z README — ✅
- [ ] 5 mock interviews przeprowadzonych (z kolegą lub nagranie siebie) — ✅
- [ ] Zaktualizowana lista ofert — aplikowanie na 20+ ofert w miesiącu 12 — ✅
- [ ] Stawka wynegocjowana: B2B 110+ PLN/h LUB nowa umowa — ✅

---

# 🅱️ TRACK B: Data QA (Miesiące 7–12)

## Miesiąc 7–8 — SQL Advanced + Data Validation Patterns

> **Zasoby**:
> - [pgExercises advanced](https://pgexercises.com/) (bezpłatny)
> - [SQL Data Quality patterns](https://learnsql.com/blog/data-quality-sql/) (bezpłatny)

### Checklisty Miesiące 7–8
- [ ] Window functions — zaawansowane ćwiczenia (LEAD/LAG, FIRST_VALUE, LAST_VALUE) — ✅
- [ ] CTEs rekurencyjne — hierarchiczne zapytania — ✅
- [ ] Data quality SQL patterns — null checks, duplicate detection, referential integrity — ✅
- [ ] pgExercises — wszystkie sekcje ukończone — ✅
- [ ] Własna biblioteka "test queries" — 30 gotowych wzorców w repo — ✅

---

## Miesiąc 9 — dbt Fundamentals

> **Zasoby**:
> - [dbt Fundamentals — BEZPŁATNY kurs](https://courses.getdbt.com/) (oficjalny, certyfikowany)
> - [dbt docs](https://docs.getdbt.com/) (bezpłatny)

### Tematy miesiąca
- dbt models — transformacje SQL jako pliki .sql
- `dbt test` — built-in tests: not_null, unique, accepted_values, relationships
- `dbt docs generate` — automatyczna dokumentacja
- Jinja macros w dbt — reużywalne kawałki SQL
- Sources i staging models — konwencje nazewnictwa
- dbt Core (local) — bezpłatna wersja

### Checklisty Miesiąc 9
- [ ] dbt Fundamentals kurs ukończony (certyfikat) — ✅
- [ ] Lokalny projekt dbt z 5+ modelami — ✅
- [ ] `dbt test` — testy not_null, unique, relationships dla wszystkich modeli — ✅
- [ ] Własne makro Jinja napisane — ✅

---

## Miesiąc 10 — ETL Testing Patterns

> **Zasoby**:
> - [PySpark Getting Started](https://spark.apache.org/docs/latest/api/python/getting_started/) (bezpłatny)
> - pytest + dbt integration (własna implementacja)

### Tematy miesiąca
- Row count validation przed i po transformacji
- Null check dla kluczowych kolumn
- Duplicate detection (GROUP BY + HAVING COUNT > 1)
- Referential integrity checks
- Data range validation (sensowne zakresy dat, wartości numerycznych)
- PySpark basics — RDD, DataFrame API, read/write CSV/Parquet
- pytest + dbt: jak uruchamiać dbt tests z pytest

### Checklisty Miesiąc 10
- [ ] Napisałem 20 ETL test patterns jako pytest fixtures — ✅
- [ ] PySpark: odczyt CSV, transformacja, zapis Parquet — ✅
- [ ] pytest + dbt integration — testy uruchamiają się razem — ✅

---

## Miesiąc 11 — Snowflake + Cloud Data

> **Zasoby**:
> - [Snowflake Free Trial](https://trial.snowflake.com/) (30 dni, bezpłatny)
> - [BigQuery Sandbox](https://cloud.google.com/bigquery/docs/sandbox) (bezpłatny — bez karty płatniczej)

### Checklisty Miesiąc 11
- [ ] Snowflake trial konto założone — ✅
- [ ] Załaduj przykładowe dane do Snowflake, napisz 10 test queries — ✅
- [ ] BigQuery Sandbox — public datasets, 10 zapytań analitycznych — ✅
- [ ] Zrozumienie: co to kolumnowa baza danych i dlaczego jest szybsza dla analityki — ✅

---

## Miesiąc 12 — Portfolio #3 Data QA + Mock Interviews

### Portfolio #3 — Data QA

**Wymagania**:
- dbt projekt z 5+ modelami + testy dbt
- pytest data validation suite (20+ test assertions)
- Dokumentacja: README z architekturą data pipeline
- CI: GitHub Actions

### Checklisty Miesiąc 12
- [ ] Portfolio #3 Data QA opublikowany na GitHub — ✅
- [ ] Mock interviews: SQL (window functions, ETL patterns), Python (pytest fixtures), dbt — ✅
- [ ] Aplikowanie — 20+ ofert "Data QA / Data Engineer in Test" — ✅
- [ ] Stawka: B2B 110–150 PLN/h — ✅

---

# ☁️ AWS Basics (Oba Tracki — Miesiąc 11–12)

> **Zasoby**:
> - [AWS Free Tier](https://aws.amazon.com/free/) (12 miesięcy bezpłatnie)
> - [AWS Skill Builder](https://explore.skillbuilder.aws/learn) (bezpłatny kurs "AWS Cloud Practitioner Essentials")

### Tematy AWS dla testerów
- S3: odczyt/zapis plików w testach (boto3), generowanie presigned URLs
- Lambda: testowanie event-driven functions (invoke, check logs)
- CloudWatch: znajdowanie logów aplikacji pod test
- IAM: jak działają role i uprawnienia (żebyś wiedział o co pytać devopsów)

### Checklisty AWS
- [ ] Konto AWS Free Tier założone — ✅
- [ ] S3 bucket stworzony, odczytany przez pytest (boto3) — ✅
- [ ] Lambda function zinwokowana z pytest — ✅
- [ ] CloudWatch — znalazłeś logi aplikacji i zinterpretowałeś je — ✅
- [ ] AWS Cloud Practitioner Essentials kurs (Skill Builder) — ✅

---

## 💰 Projekcja po Miesiącach 7–12

```
🏆 TRACK A (Java)
   B2B: 110–130 PLN/h ≈ 17 600–20 800 PLN netto
   Stack: Python + Playwright + TypeScript + Java + REST Assured + JUnit 5 + Docker + CI/CD
   Portfolio: 3 publiczne projekty na GitHub

🏆 TRACK B (Data QA)
   B2B: 110–150 PLN/h ≈ 17 600–24 000 PLN netto
   Stack: Python + pytest + SQL + dbt + Spark + Snowflake + Cloud
   Portfolio: 3 publiczne projekty + certyfikat dbt Fundamentals

🎯 CEL 10 000 PLN NETTO — PRZEKROCZONY
```

## ✅ Podsumowanie Miesiące 7–12

- [ ] Track wybrany i ukończony (Java lub Data QA)
- [ ] Portfolio #3 opublikowany
- [ ] AWS basics ukończone
- [ ] Mock interviews przeprowadzone
- [ ] 20+ aplikacji wysłanych w miesiącu 12
- [ ] Stawka B2B 110+ PLN/h wynegocjowana

---

## 📊 Pokrycie Technologii po 12 Miesiącach

| Technologia | Status |
|-------------|--------|
| SQL | ✅ Advanced (window functions, CTEs, data quality) |
| REST API | ✅ Advanced (Python requests + Java REST Assured) |
| Playwright Python | ✅ Expert |
| Playwright TypeScript | ✅ Advanced |
| pytest | ✅ Expert (fixtures, markers, parametrize, BDD) |
| Docker | ✅ Intermediate |
| BDD/Gherkin | ✅ Intermediate |
| Jenkins | ✅ Advanced (Jenkinsfile) |
| Java + JUnit 5 | ✅ Intermediate (Track A) |
| dbt | ✅ Intermediate (Track B) |
| AWS | ✅ Basics |
| TypeScript | ✅ Intermediate |

> ➡️ Następny plik: [qa_plan_05_2_lata.md](qa_plan_05_2_lata.md) — Senior Level + Future-Proof
