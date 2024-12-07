# Porównywanie tekstów, sortowanie leksykograficzne i wyszukiwanie wzorca

## Projekt zawiera implementacje trzech podstawowych operacji na tekstach:

### 1. Wyszukiwanie wzorca metodą naiwną

Algorytm służy do sprawdzania, czy w danym tekście występuje określony wzorzec. Jest to najprostsza metoda, polegająca na porównywaniu fragmentów tekstu z wzorcem.

**Główne pętle algorytmu:**
- Pętla zewnętrzna iteruje przez wszystkie możliwe pozycje w tekście, zaczynając od indeksu 0 i kończąc na `n - m + 1` (gdzie `n` to długość tekstu, a `m` to długość wzorca).
- Pętla wewnętrzna porównuje kolejne znaki tekstu z wzorcem, aż do pełnego dopasowania lub wykrycia różnicy.

**Kluczowa pętla:**

```python
for i in range(n - m + 1):  # iteracja po możliwych pozycjach w tekście
    for j in range(m):  # porównanie znaków wzorca z fragmentem tekstu
        if tekst[i + j] != wzorzec[j]:  # przerwanie, gdy znak się nie zgadza
            break
        elif j == m - 1:  # dopasowanie znalezione
            return True
```
Weźmy tekst "INFORMACJA" i wyszukajmy tekst "MA" kolejno należy porównywać następujące fragmenty:

![image](https://github.com/user-attachments/assets/322fa00c-c356-48db-ac88-2ac8c7466055)

Przeanalizujmy przykład dla tekstu "bababac", w którym chcemy sprawdzić, czy występuje fraza "bac".

![image](https://github.com/user-attachments/assets/faaf0af3-7e36-499b-b2fd-0497f797cc83)

Algorytm będzie sprawdzał, czy pierwsza litera w tekście jest taka sama jak pierwsza litera we wzorcu, jeśli jest zgodność, to sprawdzamy zgodność kolejnych liter. Jeśli po drodze napotkamy niezgodność, to zabawę zaczynamy od nowa porównując odpowiednie litery ze wzroca ze znakami z tekstu począwszy od kolejnej litery:

![image](https://github.com/user-attachments/assets/45f0c123-df87-48e1-b570-3206469497d5)

Więcej szczegółów znajduje się w pliku [wyszukiwanie_wzorca_1.py](wyszukiwanie_wzorca_1.py) oraz [wyszukiwanie_wzorca_2.py](wyszukiwanie_wzorca_2.py).

### 2. Sortowanie leksykograficzne

Sortowanie leksykograficzne porządkuje słowa zgodnie z ich alfabetyczną kolejnością. W tym przypadku zaimplementowano algorytm sortowania bąbelkowego, który iteruje po liście i zamienia miejscami elementy, które są w złej kolejności.

**Główne pętle algorytmu:**
- Pętla zewnętrzna przechodzi przez wszystkie słowa w liście.
- Pętla wewnętrzna porównuje kolejne pary słów, a jeśli są one w złej kolejności, zamienia je miejscami.

**Kluczowa pętla:**

```python
for i in range(n):  # zewnętrzna pętla, iteracja po wszystkich elementach listy
    for j in range(0, n - i - 1):  # porównanie sąsiednich słów
        if slowa[j] > slowa[j + 1]:  # zamiana miejscami, jeśli słowa są w złej kolejności
            slowa[j], slowa[j + 1] = slowa[j + 1], slowa[j]
```

Dodatkowo, Python oferuje wbudowaną funkcję `sorted()`, która ułatwia sortowanie listy słów w porządku leksykograficznym. Zamiast implementować algorytm sortowania samodzielnie, wystarczy użyć tej funkcji, jak pokazano poniżej:

```python
posortowane_slowa = sorted(slowa)
print(posortowane_slowa)
```

Więcej szczegółów znajduje się w pliku [sortowanie_leksykograficzne.py](sortowanie_leksykograficzne.py).

### 3. Porównywanie tekstów

Algorytm porównuje dwa teksty, sprawdzając, czy są one identyczne. Jeśli porównanie ma uwzględniać wielkość liter, teksty muszą mieć takie same litery w tych samych miejscach.

**Główne pętle algorytmu:**
- Pętla iteruje przez wszystkie znaki w obu tekstach i porównuje je.
- Jeśli napotka różnicę, zwraca wynik False; jeśli wszystkie znaki się zgadzają, zwraca True.

**Kluczowa pętla:**

```python
for i in range(len(tekst1)):  # iteracja po wszystkich znakach obu tekstów
    if tekst1[i] != tekst2[i]:  # porównanie znaków
        return False
```

Warto zauważyć, że porównywanie tekstów można uprościć, wykorzystując bezpośrednie porównanie w Pythonie:

```python
if tekst1 == tekst2:
    print("Teksty są identyczne")
else:
    print("Teksty różnią się")
```

Dzięki temu kod jest prostszy i bardziej przejrzysty.

Więcej szczegółów znajduje się w pliku [porownywanie_tektow.py](porownywanie_tektow.py).

Źródła wiedzy:
https://mattomatti.com/pl/a0011?plang=py#elcode1
https://www.algorytm.edu.pl/algorytmy-w-python/wyszukiwanie-wzorca-w-tekscie-python
https://pl.wikipedia.org/wiki/Sortowanie_leksykograficzne
