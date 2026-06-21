# 🚴 AdventureWorks — Zaawansowany Raport Analizy Finansowej, Retencji i Produktów

Kompleksowy, 3-stronicowy raport Power BI zaprojektowany w celu monitorowania kondycji finansowej, efektywności kanałów sprzedaży, retencji klientów oraz rentowności asortymentu w przedsiębiorstwie AdventureWorks.

## 🕹️ Interaktywna Prezentacja Raportu (Wideo)

Poniższe nagranie prezentuje dynamiczne zachowanie osi wykresu punktowego oraz automatyczne filtrowanie danych między wizualizacjami:

<video src="raport_prezentacja.mp4" controls autoplay loop muted width="100%"></video>

*(Pamiętaj, aby nazwa pliku wideo wrzuconego na GitHub była identyczna jak w kodzie powyżej, np. `raport_prezentacja.mp4`)*

---

## 📁 Dostępne Formaty Projektu

* 📥 **[Pobierz plik źródłowy .pbix](AdventureWorks_Raport.pbix)** — pobierz projekt na komputer, aby zweryfikować model danych, relacje gwiazdy oraz zaawansowany kod miar DAX.
* 📄 **[Pobierz raport w formacie PDF](AdventureWorks_Raport.pdf)** — szybki podgląd całego układu stron w formacie dokumentu biznesowego.

---

## 📊 Architektura i Biznesowa Logika Stron Raportu

### Strona 1: Podsumowanie Wyników Finansowych i Operacyjnych
Układ typu *Executive Summary* dający kadrze zarządzającej natychmiastowy wgląd w kluczowe metryki firmy.
* **Kluczowe KPI:** Monitoring Total Sales (110 mln), Total Profit (13 mln) oraz Średniej Wartości Koszyka (Average Basket Value).
* **Wizualizacje:** Zaawansowana analiza trendu sprzedaży mieścin do miesiąca (Sales vs LY), rozkład geograficzny na mapie oraz ranking rentowności klientów typu Reseller.

### Strona 2: Analiza Efektywności Sprzedaży i Retencji
Widok dedykowany działom marketingu i operacji, skupiony na dynamice zmian i lojalności partnerów handlowych.
* **Analiza Retencji:** Unikalny wykres liniowy zestawionego napływu nowych kontrahentów (*New Resellers*) w relacji do bazy partnerów aktywnych (*Active Resellers*) w czasie.
* **Sygnalizacja KPI:** Wykorzystanie formatowania warunkowego czcionki w celu natychmiastowego wyróżnienia dynamiki wzrostu (Sales YoY % na poziomie +43%).

### Strona 3: Głęboka Analiza Produktowa i Rentowności
Moduł analityczny służący do optymalizacji portfela asortymentu i wykrywania anomalii marżowych.
* **KPI Scatter Chart:** Wykres punktowy mapujący wolumen sztuk (*Total Quantities*) versus rentowność (*Profit Margin %*). Podkategorie generujące straty operacyjne automatycznie wyróżniono alarmującym kolorem czerwonym (*Jerseys*, *Caps*).
* **Linie Odniesienia (Kwadranty):** Zastosowanie analitycznych linii średniej, które automatycznie dzielą wykres na 4 strefy menedżerskie (np. produkty wysokowolumenowe, ale niskomarżowe).
* **System Naczyń Połączonych:** Interaktywny wykres punktowy jest w pełni zsynchronizowany z tabelą Matrix po prawej stronie. Kliknięcie dowolnego bąbelka natychmiast filtruje tabelę szczegółową, umożliwiając pełny *drill-down* do konkretnych nazw modeli.

---

## 🛠️ Wybrane Zaawansowane Miary DAX

W raporcie zaimplementowano niestandardową logikę eliminującą ograniczenia natywnych wizualizacji Power BI:

### 1. Dynamiczne skalowanie osi X (Zapobieganie ucinaniu bąbelków)
```dax
Dynamic X Max = 
VAR MinVal = MINX(ALLSELECTED(Product[Subcategory]), [Total Quantities])
VAR MaxVal = MAXX(ALLSELECTED(Product[Subcategory]), [Total Quantities])
VAR Range = MaxVal - MinVal
RETURN
MaxVal + (Range * 0.25)
```

### 2. Formatowanie warunkowe bąbelków i czcionek (Wyróżnienie strat)
```dax
Color KPI = IF([Profit Margin %] < 0, "#FF4D4D", "#002D62")
```

### 3. Procentowa dynamika wolumenu rok do roku
```dax
Quantities YoY % = 
VAR QuantitiesLY = CALCULATE([Total Quantities], SAMEPERIODLASTYEAR('Calendar'[Date]))
RETURN
DIVIDE([Total Quantities] - QuantitiesLY, QuantitiesLY, 0)
```

https://github.com/user-attachments/assets/1513d4c3-8b7b-4da7-8108-0580d1deae1e



