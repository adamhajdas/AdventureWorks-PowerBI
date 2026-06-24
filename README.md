# Raport Analizy Finansowej, Retencji i Produktów dla bazy AdventureWorks

3-stronicowy raport Power BI zaprojektowany w celu monitorowania kondycji finansowej, efektywności kanałów sprzedaży, retencji klientów oraz rentowności asortymentu. 
Wykorzystałem DAX i różne metody wizualizacji w PowerBI, żeby pokazać warsztat i otwartość na stosowanie różnych narzędzi analizy danych. 

## Interaktywna Prezentacja Raportu (Wideo)

Poniższe nagranie prezentuje dynamiczne zachowanie danych, możliwości jakie raport daje dla użytkownika.

[<video src="raport_prezentacja.mp4" controls autoplay loop muted width="100%"></video>](https://github.com/user-attachments/assets/1513d4c3-8b7b-4da7-8108-0580d1deae1e)

---

## 📁 Dostępne Formaty Projektu

* 📥 **[Pobierz plik źródłowy .pbix](AdventureWorks_Raport.pbix)**
* 📄 **[Pobierz raport w formacie PDF](AdventureWorks_Raport.pdf)**

---

## 📊 Architektura i Biznesowa Logika Stron Raportu

### Strona 1: Podsumowanie Wyników Finansowych i Operacyjnych
Układ typu *Executive Summary* dający kadrze zarządzającej natychmiastowy wgląd w kluczowe metryki firmy.
* **Kluczowe KPI:** Monitoring Total Sales (110 mln), Total Profit (13 mln) oraz Średniej Wartości Koszyka (Average Basket Value).
* **Wizualizacje:** Analiza trendu sprzedaży (Sales vs LY), rozkład geograficzny na mapie oraz ranking rentowności klientów typu Reseller.

### Strona 2: Analiza Efektywności Sprzedaży i Retencji
Widok skupiony na dynamice zmian (YTD, sales LY) i skali pozyskiwania nowych klientów hurtowych.
* **Analiza Retencji:** Wykres liniowy napływu nowych kontrahentów (*New Resellers*) w czasie.
* **Sygnalizacja KPI:** Wykorzystanie formatowania warunkowego czcionki w celu wyróżnienia (Sales YoY % na zielono/czerwono)

### Strona 3: Głęboka Analiza Produktowa i Rentowności
Moduł pozwalający na analizę w kontekście asortymentu i wykrywanie anomalii marżowych.
* **KPI Scatter Chart:** Wykres punktowy mapujący wolumen sztuk (*Total Quantities*) versus rentowność (*Profit Margin %*). Podkategorie generujące straty operacyjne automatycznie wyróżniono alarmującym kolorem czerwonym (*Jerseys*, *Caps*).
* **Linie Odniesienia (Kwadranty):** Zastosowanie analitycznych linii średniej, które automatycznie dzielą wykres na 4 strefy menedżerskie (np. produkty wysokowolumenowe, ale niskomarżowe).
* **System Naczyń Połączonych:** Interaktywny wykres punktowy jest w pełni zsynchronizowany z tabelą Matrix po prawej stronie. Kliknięcie dowolnego bąbelka natychmiast filtruje tabelę szczegółową, umożliwiając pełny *drill-down* do konkretnych nazw modeli.

---
