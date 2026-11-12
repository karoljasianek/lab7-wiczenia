# Laboratorium 7: drzewa decyzyjne – kto odejdzie z programu lojalnościowego?

## Krok po kroku
1. **Use this template / Fork** to repozytorium na swoje konto GitHub.
2. **Code → Codespaces → Create codespace on main**. Poczekaj, aż otworzy się VS Code w przeglądarce.
3. W terminalu (na dole ekranu):
   ```bash
   pip install -r requirements.txt
   ```
4. Otwórz `lab7_student.ipynb`, wybierz jądro **Python 3** i wykonuj komórki po kolei (*Shift + Enter*). Uzupełnij luki `___`.
5. Aplikacja (zadanie Z10):
   ```bash
   streamlit run app.py
   ```
   Codespaces zaproponuje otwarcie portu **8501**: kliknij *Open in Browser*.
6. Zapisz pracę w repozytorium:
   ```bash
   git add .
   git commit -m "Lab 7: drzewa decyzyjne"
   git push
   ```
7. **Render:** *New → Web Service* → wybierz swoje repozytorium. Ustawienia są w `render.yaml` (plan *Free*).
   Pierwsze uruchomienie trwa kilka minut. Link do aplikacji wklej do karty zadań.

## Pliki
| Plik | Co to jest |
|---|---|
| `lab7_student.ipynb` | notatnik z zadaniami Z1–Z10 |
| `klienci_odejscia.csv` | 1206 klientów programu lojalnościowego (dane syntetyczne) |
| `dziesieciu_klientow.csv` | 10 klientów do rozgrzewki (Z1) |
| `app.py` | kalkulator ryzyka odejścia (Streamlit) |
| `requirements.txt`, `render.yaml` | biblioteki i ustawienia wdrożenia na Render |

## Moje odpowiedzi

| Zad. | Pytanie | Odpowiedź |
|---|---|---|
| Z1 | który podział i dlaczego | **liczba_zamowien ≤ 2**: ważony indeks Giniego 0,32 jest mniejszy niż przy „dni > 180” (0,417), więc grupy są bardziej jednorodne. G całej grupy = 0,50. |
| Z3 | najbardziej ryzykowny liść | **dni_od_ostatniego > 175,5 i liczba_zamowien ≤ 2,5**: 163 klientów, odeszło 136, czyli **83%**. |
| Z5 | najlepsza głębokość, zjawisko | **Głębokość 3** (walidacja 77,7%). Głębsze drzewo: trafność na zbiorze uczącym rośnie do 100%, a walidacyjna spada do 71,3%. To **przeuczenie**. |
| Z6 | kto w najmniejszym liściu | **1 klient** z wydatkami > 83 274 zł (92 206 zł, 56 zamówień, koszyk 1647 zł). To wartość odstająca z lab. 3 (bardzo duży klient, prawdopodobnie firma lub hurtownik). Reguła z jednego przypadku to anegdota, dlatego `min_samples_leaf=20`. Najważniejsza cecha: dni_od_ostatniego (0,86). |
| Z7 | który błąd droższy | **Przeoczenie** (52 osoby): tracimy ok. 0,3 · 250 − 30 = 45 zł oczekiwanego zysku na kliencie. Fałszywy alarm (27 osób) kosztuje 30 zł za kupon. |
| Z8 | najlepszy próg, zysk | **Próg 0,4: 2025 zł** (125 kuponów). Kupon opłaca się już przy ryzyku > 0,4. Kupon dla wszystkich daje −2310 zł, więc model zarabia o 4335 zł więcej. |
| Z9 | czy można użyć kolumny | **Nie.** `dni_od_logowania_31_03_2027` jest znana dopiero po okresie, który przewidujemy (99,4% trafności to złudzenie). To **wyciek danych**. |
| Z10 | link do aplikacji na Render | https://ryzyko-odejscia.onrender.com |

Odpowiedzi do zadania domowego (D1–D3) są w notatniku `lab7_student.ipynb`, w ostatniej komórce.
