# 📅 Miesiące 13–24 — Senior Level + Future-Proof

> **Cel**: Senior QA Engineer / QA Architect, niche specialization, 120–160 PLN/h  
> **Format**: Kwartalny — na tym etapie sam steruj tempem i kierunkiem

---

## 📊 Gdzie jesteś po 12 Miesiącach

```
✅ Python + pytest (expert) — już masz
✅ Playwright Python (expert)
✅ TypeScript + Playwright TS (advanced)
✅ SQL (advanced)
✅ Docker + CI/CD (intermediate)
✅ BDD/Gherkin (intermediate)
✅ REST API (advanced)
✅ Java/Data QA (intermediate — wybrany track)
✅ AWS Basics
✅ 3 publiczne projekty portfolio
✅ B2B 110+ PLN/h — powinno być wynegocjowane
```

---

## Q1 (Miesiące 13–15) — Performance Testing

> **Dlaczego teraz?** Performance testing jest niszą z premium stawkami (+20–30 PLN/h) i małą konkurencją wśród QA.

### Główne narzędzie: k6

> **Zasoby**:
> - [k6 docs](https://k6.io/docs/) (bezpłatny, nowoczesny, JS-based, CI-friendly)
> - [k6 official YouTube channel](https://www.youtube.com/c/k6test) (bezpłatny)
> - [Grafana + k6 integration](https://grafana.com/docs/k6/latest/results-output/real-time/grafana-cloud/) (Grafana Cloud: free tier)

### Miesiąc 13 — k6 Podstawy

**Dziennie: pełny format 2-godzinny (Blok 1 + Przerwa + Blok 2 + Podsumowanie)**

- [ ] Instalacja k6, pierwszy load test
- [ ] Virtual Users (VUs), iterations, duration
- [ ] HTTP requests w k6: `http.get()`, `http.post()`, checks
- [ ] Thresholds — definiowanie SLA: `p95 < 500ms`, `error_rate < 0.01`
- [ ] Scenarios: constant-vus, ramping-vus, constant-arrival-rate

### Miesiąc 14 — k6 Advanced + Grafana

- [ ] k6 stages — ramp-up, steady state, ramp-down
- [ ] Test types: load test, stress test, spike test, soak test
- [ ] k6 extensions: xk6 ecosystem
- [ ] Grafana Cloud k6 — wysyłanie wyników do dashboardu
- [ ] Lokalny Grafana + InfluxDB przez docker-compose
- [ ] GitHub Actions + k6: threshold failures jako CI failures

### Miesiąc 15 — k6 Projekt + Raportowanie

- [ ] Pełny load test suite dla reqres.in lub aplikacji z portfolio
- [ ] Dashboard Grafana z metrykami: p50, p95, p99, error rate, throughput
- [ ] Dokumentacja: co testowałeś, jakie wnioski, jak interpretować wyniki
- [ ] README z wynikami testów i screenshotami dashboardu

### Checklisty Q1
- [ ] Pierwszy load test z k6 napisany — ✅
- [ ] Thresholds skonfigurowane (max p95 < 500ms) — ✅
- [ ] GitHub Actions + k6 pipeline — test failures blokują merge — ✅
- [ ] Grafana dashboard lokalny — widoczny w portfolio — ✅
- [ ] Rozumiem: load test vs stress test vs spike test vs soak test — ✅

---

## Q2 (Miesiące 16–18) — AI w Testowaniu

> **Dlaczego teraz?** AI w testach to najszybciej rosnący segment — firmy płacą premium za kandydatów którzy rozumieją ZARÓWNO testowanie JAK I AI.

### Zasoby
- [GitHub Copilot](https://github.com/features/copilot) — free tier dla open source lub student
- [Microsoft Promptflow](https://github.com/microsoft/promptflow) (bezpłatny, open source)
- [TestingAI.co](https://testingai.co/) (artykuły i praktyki — bezpłatny)

### Miesiąc 16 — GitHub Copilot w Pracy QA

**Dziennie: pełny format 2-godzinny**

- [ ] GitHub Copilot skonfigurowany w VS Code lub IntelliJ
- [ ] Generowanie test cases z komentarzy: `# test that login fails with wrong password`
- [ ] Refactoring testów z Copilot — porównaj przed/po
- [ ] Generowanie Page Objects z HTML — ocena jakości
- [ ] 20 test cases wygenerowane przez Copilot i przejrzane krytycznie
- [ ] Dokument: "Kiedy Copilot pomaga, kiedy szkodzi" — własna analiza

### Miesiąc 17 — Testowanie Systemów AI/LLM

- [ ] Co to jest prompt injection — jak testować?
- [ ] Hallucination detection — jak weryfikować odpowiedzi LLM?
- [ ] AI test oracle patterns — jak sprawdzić czy AI output jest "poprawny"?
- [ ] Podstawy ewaluacji modeli: accuracy, precision, recall w kontekście testowania
- [ ] Microsoft Promptflow — napisz prosty flow, przetestuj

### Miesiąc 18 — AI Testing Portfolio

- [ ] 1 aplikację LLM przetestowaną (hallucination + prompt injection scenarios)
- [ ] Test suite dla AI feature (np. chatbot, search z AI, rekomendacje)
- [ ] Artykuł lub README opisujący podejście do testowania AI

### Checklisty Q2
- [ ] GitHub Copilot skonfigurowany w IDE — ✅
- [ ] 20 test cases wygenerowane przez Copilot i zreviewowane — ✅
- [ ] 1 LLM application przetestowana (hallucination + prompt injection) — ✅
- [ ] Artykuł techniczny o testowaniu AI napisany — ✅

---

## Q3 (Miesiące 19–21) — Deep Specialization

> Wybierz jedną ścieżkę specjalizacji na podstawie: feedbacku z rynku, własnych zainteresowań, i stawek.

### Opcja A: Data QA Architect

> Dla osób na Track B lub tych którym market feedback wskazuje na zapotrzebowanie na data.

- [ ] Snowflake certyfikacja (ocena ROI) — [SnowPro Core](https://www.snowflake.com/certifications/)
- [ ] Databricks Community Edition — [databricks.com/try-databricks](https://www.databricks.com/try-databricks) (bezpłatny)
- [ ] PySpark advanced: joins, window functions, UDFs
- [ ] Projektowanie architektury testów data pipeline end-to-end
- [ ] Data contract testing patterns

### Opcja B: Security Testing Basics

> Dla osób zainteresowanych bezpieczeństwem — premium stawki, mała konkurencja.

- [ ] [OWASP Top 10](https://owasp.org/www-project-top-ten/) — przeczytaj całość (bezpłatny)
- [ ] [OWASP ZAP](https://www.zaproxy.org/) — bezpłatne, open source narzędzie security testing
- [ ] SQL injection testing (ręczne + automatyczne)
- [ ] XSS testing patterns
- [ ] CSRF, IDOR, authentication bypass — podstawy
- [ ] ZAP automated scan zintegrowany z CI

### Opcja C: QA Lead / Test Strategy

> Dla osób dążących do ról leadership — wymagana wcześniejsza silna pozycja na rynku.

- [ ] [Test Pyramid — Martin Fowler](https://martinfowler.com/articles/practical-test-pyramid.html) (bezpłatny artykuł)
- [ ] Risk-based testing — jak priorytetyzować co testować
- [ ] Test strategy document — napisz dla fikcyjnego projektu
- [ ] Metryki testowania: defect escape rate, test coverage, flaky test rate
- [ ] Prowadzenie code review dla testów (junior QA) — mockuj z kolegą

### Checklisty Q3
- [ ] Wybrałem specjalizację: _______ [Data QA / Security / QA Lead]
- [ ] Ukończyłem podstawowy kurs wybranej specjalizacji — ✅
- [ ] Mam projekt portfolio pokazujący specjalizację — ✅
- [ ] Zaktualizowałem CV i LinkedIn o wybraną specjalizację — ✅

---

## Q4 (Miesiące 22–24) — Leadership + Visibility

> Na tym etapie chodzi o widoczność w społeczności, nie tylko techniczne umiejętności.

### ISTQB Advanced — Decyzja

> **CTAL-TA (Test Analyst)** lub **CTAL-TAE (Test Automation Engineer)**
> - [istqb.org](https://www.istqb.org/) — lista egzaminów i sylabusów (sylabusy bezpłatne)
> - Koszt egzaminu: ok. 800–1200 PLN
> - ROI: Pomaga w dużych korporacjach i przetargach publicznych; mniej ważne w startupach/agile

- [ ] Sprawdziłem czy moje targety (firmy) wymagają ISTQB Advanced
- [ ] ISTQB Advanced — decyzja podjęta: warto / nie warto dla mojego targetu

### LinkedIn Visibility

- [ ] Post 1 — case study z projektu performance testing (k6 + wyniki)
- [ ] Post 2 — "Czego nauczyłem się testując AI system" (z konkretnym przykładem)
- [ ] Post 3 — porównanie Python vs TypeScript w Playwright (techniczna treść)
- [ ] Post 4 — wybrany temat specjalizacji (Data QA / Security / QA Lead)
- [ ] Wszystkie posty z kodem lub screenami — nie tylko "soft" treści

### Open Source Contribution

- [ ] Znalazłem projekt do kontrybucji: playwright-python, pytest-bdd, k6, lub inny testing framework
- [ ] Otworzyłem issue opisując problem lub improvement
- [ ] Pull Request wysłany — poprawka buga, dokumentacja, nowy test, lub mała funkcjonalność
- [ ] Pull Request zaakceptowany i zmergowany — ✅

### Community

- [ ] Znalazłem lokalny meetup QA: szukaj "QA meetup Trójmiasto", "Testing meetup Gdańsk" na Meetup.com
- [ ] Prelekcja na meetupie LUB artykuł techniczny opublikowany (dev.to, medium, własny blog)
- [ ] Mentoring — zaproponowałem pomoc 1 juniorowi QA (LinkedIn lub meetup)

### Checklisty Q4
- [ ] 4 posty na LinkedIn napisane i opublikowane — ✅
- [ ] 1 Pull Request do open source projektu zaakceptowany — ✅
- [ ] Prelekcja na meetupie LUB artykuł techniczny — ✅
- [ ] ISTQB Advanced — decyzja podjęta — ✅

---

## 🛡️ Bezpieczeństwo Zatrudnienia — Jak Nie Bać Się Utraty Pracy

> Ten rozdział to nie teoria — to konkretny plan awaryjny który sprawia że "utrata pracy" staje się  
> "2-4 tygodniowy płatny wakans między kontraktami".

### 7 Filarów Bezpieczeństwa

**1. Dwa golden stacks = dwa rynki**  
Python+Playwright + TypeScript+Playwright = oferty na obu rynkach jednocześnie.  
Jeden rynek wysycha? Drugi nadal płaci.

**2. Python = future-proof w erze AI**  
Narzędzia AI pisane w Pythonie: LangChain, Transformers, FastAPI, dbt.  
Tester znający Python jest VALUE dla AI projectów, nie COST.  
Testowanie AI systemów (prompt injection, hallucination) = nowa nisza.

**3. SQL = zawsze**  
Bazy danych były przed cloudem, przed Dockerem, przed AI.  
Każdy system przechowuje dane. Senior QA z SQL nigdy nie jest bezrobotny.

**4. GitHub = żywe CV**  
Aktywny GitHub z 3+ projektami = rekruter widzi Twoje umiejętności BEZ rozmowy.  
W kryzysie: 2 tygodnie → oferta. Bez GitHub: 6-8 tygodni.

**5. Jenkins już masz** (50% ofert wymaga!)  
To ukryta wartość w Twoim profilu — większość kandydatów tego NIE ma.  
Wymień to explicite w CV i LinkedIn.

**6. Aktywna obecność na rynku**  
Raz na kwartał: przejrzyj 20 ofert MID/SENIOR i sprawdź czy Twoje CV pasuje do 70%+.  
Nie czekaj na kryzys żeby sprawdzić gdzie jesteś.

**7. Sieć kontaktów**  
5+ rekruterów QA w Polsce którzy znają Cię z imienia = early warning system.  
Gdy firma zaczyna zwalniać → rekruterzy wiedzą 2-3 miesiące wcześniej.

### Plan Awaryjny (Emergency 30-Day Job Search)

```
Dzień 1–3:  Odśwież CV + LinkedIn (2h)
Dzień 4–7:  Wyślij 20 aplikacji na JustJoin + NoFluffJobs + BulldogJob
Dzień 8–14: 3–5 rozmów telefonicznych (filtr)
Dzień 15–21: 2–3 rozmowy techniczne
Dzień 22–28: Oferta + negocjacja
Dzień 29–30: Podpisanie umowy
```

### Checklisty Bezpieczeństwa Zatrudnienia
- [ ] GitHub aktywny — co najmniej 3 publiczne projekty z ostatnich 12 miesięcy — ✅
- [ ] LinkedIn — połączony z 5+ rekruterami QA w Polsce — ✅
- [ ] Raz na 3 miesiące: przejrzyj 20 ofert MID i zaktualizuj CV jeśli trzeba — ✅
- [ ] Emergency plan gotowy: wiem że mogę znaleźć pracę w 4 tygodnie — ✅
- [ ] CV i LinkedIn zawsze aktualne (nie czekam na kryzys) — ✅

---

## 💰 Finalna Projekcja Wynagrodzenia

```
⚡ Miesiąc 0      — negocjacja: 12 000–14 000 PLN brutto | B2B: 85–95 PLN/h
📈 Miesiąc 3      — B2B: 90–100 PLN/h ≈ 14 400–16 000 PLN netto
✅ Miesiąc 6      — B2B: 100–110 PLN/h ≈ 16 000–17 600 PLN netto | 10k CEL OSIĄGALNY
🏆 Miesiąc 12     — B2B: 110–130 PLN/h ≈ 17 600–20 800 PLN netto | 10k PRZEKROCZONE
⭐ Miesiąc 24     — B2B: 120–160 PLN/h ≈ 19 200–25 600 PLN netto | Senior/Specjalizacja
```

## 📊 Pełne Pokrycie Technologii po 24 Miesiącach

| Technologia | Poziom | Rynek |
|-------------|--------|-------|
| Python + pytest | ⭐⭐⭐⭐⭐ Expert | 21% + wszędzie gdzie Python |
| Playwright Python | ⭐⭐⭐⭐⭐ Expert | 24% ofert |
| SQL (PostgreSQL) | ⭐⭐⭐⭐ Advanced | 45% ofert |
| TypeScript + Playwright TS | ⭐⭐⭐⭐ Advanced | 13+ ofert |
| REST API (Python+Java) | ⭐⭐⭐⭐ Advanced | 42% ofert |
| Docker + CI/CD | ⭐⭐⭐⭐ Advanced | ~70% ofert |
| BDD/Gherkin | ⭐⭐⭐ Intermediate | 12% ofert |
| Jenkins | ⭐⭐⭐⭐ Advanced (już masz!) | 50% ofert |
| Java (Track A) | ⭐⭐⭐ Intermediate | 18% ofert |
| dbt (Track B) | ⭐⭐⭐ Intermediate | data stack |
| k6 Performance | ⭐⭐⭐ Intermediate | nisza premium |
| AI w testach | ⭐⭐⭐ Intermediate | przyszłość |
| AWS | ⭐⭐ Basics | 60%+ ofert senior |
| Specjalizacja | ⭐⭐⭐⭐ Advanced | premium stawki |

---

## 🏁 Ścieżka 24-Miesięczna — Podsumowanie

```
MIESIĄC 1    → SQL + pytest → aplikuj JUŻ TERAZ na obecny profil
MIESIĄCE 2–3 → Playwright Python + Docker + Portfolio #1 → B2B możliwy
MIESIĄCE 4–6 → TypeScript + BDD + Portfolio #2 → CEL 10k netto
MIESIĄCE 7–12 → Java/Data QA + AWS + Portfolio #3 → 10k PRZEKROCZONE
MIESIĄCE 13–15 → Performance Testing (k6) → premium stawki
MIESIĄCE 16–18 → AI w testach → future-proof
MIESIĄCE 19–21 → Deep Specialization → senior/architect stawki
MIESIĄCE 22–24 → Visibility + Leadership → 120–160 PLN/h
```

---

*Plan nauki QA Automation Engineer — Senior Level Track*  
*Wszystkie zasoby są bezpłatne i publicznie dostępne.*  
*Wróć do [qa_plan_00_overview.md](qa_plan_00_overview.md) po szybki przegląd.*
