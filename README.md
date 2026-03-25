# Mikrostruktura_Czasy_Trwania_ACD_LACD
**MODELOWANIE CZASÓW TRWANIA TRANSAKCJI I CEN – ANALIZA ACD/LACD | 12/2025**

**Narzędzia**
  * R
  * tidyverse
  * ACDm
  * ggplot2
  * lubridate
  * forecast
  * e1071
  * kableExtra
  * R Markdown

**Problem**  

Konieczność zbadania dynamiki aktywności handlowej dwóch spółek giełdowych o zróżnicowanej płynności poprzez analizę transakcyjnych i cenowych czasów trwania, identyfikacja śróddziennej sezonowości oraz dopasowanie modeli ACD/LACD do odsezonowanych szeregów czasowych w celu zrozumienia mechanizmów grupowania się zdarzeń rynkowych.

**Rozwiązanie**
  * Przygotowano i oczyszczono dane tick-by-tick z okresu 6 miesięcy (01-06.2019), filtrując do godzin notowań ciągłych (9:00-16:50)
  * Obliczono transakcyjne czasy trwania jako odstępy między kolejnymi transakcjami w ramach każdej sesji
  * Wyznaczono statystyki opisowe dla czasów trwania (średnia, mediana, skośność, kurtoza, współczynnik zmienności)
  * Przeanalizowano sezonowość śróddzienną w 5-minutowych interwałach, identyfikując charakterystyczny wzorzec odwróconego U
  * Usunięto sezonowość metodą Elastycznej Formy Fouriera (FFF) z wykorzystaniem funkcji diurnalAdj z pakietu ACDm
  * Skonstruowano szeregi cenowych czasów trwania dla trzech progów cenowych
  * Dopasowano modele ACD/LACD o różnych parametrach z rozkładami: Weibulla, Burra i uogólnionym Gamma
  * Przeprowadzono diagnostykę modeli (test Andersona-Darlinga, Ljunga-Boxa, analiza ACF reszt)
  * Wygenerowano i zinterpretowano funkcje hazardu dla optymalnych modeli.

**Wynik**
  * Zidentyfikowano sezonowość w kształcie odwróconego U – najkrótsze czasy trwania przy otwarciu i zamknięciu sesji, najdłuższe w godzinach 12:00-14:00 (efekt lunchu)
  * Udokumentowano różnice w płynności, skutecznie usunięto sezonowość
  * Rozkład GenGamma zdeklasował konkurencję we wszystkich konfiguracjach, osiągając najlepsze wartości AIC
  * Wybrano modele optymalne, potwierdzono wysoką trwałość procesu (persistence)
  * Funkcje hazardu ujawniły negatywną zależność od czasu trwania – im dłuższa przerwa, tym mniejsze prawdopodobieństwo natychmiastowej transakcji
  * Projekt zrealizowano w zespole 2-osobowym z pełną dokumentacją w R Markdown.




