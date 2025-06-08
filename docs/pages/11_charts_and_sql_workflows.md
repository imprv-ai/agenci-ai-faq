---
tags:
  - Moduł 4
  - wyszukiwanie SQL
  - generowanie wykresów
  - charts.js
---

# **Workflow do generowania wykresów i wyszukiwania danych - SQL**

## **Problem z przeszukiwaniem bazy danych z node *pobierz_dane* - parse error: unexpected identifier near CASE**

1. **W SeaTable zapytania SQL nie obsługują konstrukcji CASE**, co skutkuje błędem „parse error: unexpected identifier near CASE”. Jeśli kwerenda SQL zaproponowana przez node *pobierz_dane* będzie zawierała instrukcję CASE, w N8N pojawi się ten błąd. Można zastosować obejście i odpowiednio poinstruować prompt, by nie używał niewspieranej konstrukcji podczas generowania zapytania SQL. W takim przypadku należy poprawić prompt w polu description w node *pobierz_dane*, jeśli nazwy są identyczne jak na lekcji.

      ![](assets/generate_chart_sql_case_issue.png)
      
2. Jest też możliwe, że model sam zaproponuje poprawienie kwerendy SQL – wtedy możemy zgodzić się na powtórzenie operacji bezpośrednio w czacie.
      ![](assets/generate_chart_chat.png)

## **Problem z generowaniem wykresu - brak danych**

1. Jeśli podczas próby wygenerowania wykresu, pomimo przekazania odpowiednich danych przez node *pobierz_dane*, **wykres stworzony przez node *wygeneruj_wykres* jest pusty**, możliwe, że występuje problem z poprawnym przekazaniem danych do tego node'a.

      ![](assets/generate_chart_empty_chart.png)

2. **Sprawdź w ustawieniach node *wygeneruj_wykres*, czy opcja workflow inputs jest ustawiona na - Defined automatically by the model.** W ten sposób upewniamy się, że model automatycznie sprawdzi i przekaże poprawne dane dla naszego workflow, dzięki czemu wykres zostanie wygenerowany na faktycznych danych.
      ![](assets/generate_chart_blank_chart_issue.png)

