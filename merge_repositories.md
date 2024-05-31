# Instrukcja mergowania dwóch repozytoriów w jedno

## Wstęp

Poniższa instrukcja opisuje krok po kroku, jak połączyć zawartość dwóch repozytoriów Git w jedno. Na potrzeby tej instrukcji załóżmy, że mamy repozytorium **RepozytoriumA** i chcemy przenieść jego zawartość do **RepozytoriumB**.

## Kroki

### 1. Skopiowanie repozytoriów lokalnie

Najpierw musimy skopiować oba repozytoria lokalnie. Możesz to zrobić używając komendy `git clone`.

```sh
git clone <URL-RepozytoriumA>
git clone <URL-RepozytoriumB>
```

### 2. Przejście do katalogu RepozytoriumB

Przejdź do katalogu, w którym znajduje się **RepozytoriumB**.

```sh
cd RepozytoriumB
```

### 3. Dodanie RepozytoriumA jako zdalne repozytorium

Następnie, dodajemy **RepozytoriumA** jako zdalne repozytorium do **RepozytoriumB**.

```sh
git remote add repoA <URL-RepozytoriumA>
```

### 4. Pobranie zawartości RepozytoriumA

Pobierz zawartość **RepozytoriumA** do lokalnego repozytorium.

```sh
git fetch repoA
```

### 5. Scalanie (Merge) zawartości RepozytoriumA do RepozytoriumB

Teraz możemy zmergować zawartość **RepozytoriumA** do głównej gałęzi naszego **RepozytoriumB**. Zakładamy, że chcemy zmergować zawartość master z RepozytoriumA do master w RepozytoriumB. Używamy `--allow-unrelated-histories`, ponieważ repozytoria mają różne historie commitów.

```sh
git merge repoA/master --allow-unrelated-histories
```

### 6. Rozwiązywanie konfliktów (jeśli wystąpią)

Podczas scalania mogą pojawić się konflikty. W takim przypadku Git wskaże, które pliki mają konflikty. Otwórz te pliki w edytorze, rozwiąż konflikty, a następnie zakończ proces scalania.

Po rozwiązaniu konfliktów zatwierdź zmiany:

```sh
git add .
git commit -m "Rozwiązanie konfliktów i scalanie z RepozytoriumA"
```

### 7. Usunięcie zdalnego repozytorium (opcjonalnie)

Jeśli nie potrzebujesz już zdalnego repozytorium **repoA** w konfiguracji **RepozytoriumB**, możesz je usunąć:

```sh
git remote remove repoA
```

### 8. Wypchnięcie zmian do głównego repozytorium

Na koniec, aby zatwierdzić zmiany do zdalnego repozytorium **RepozytoriumB**, wypchnij naszą scaloną wersję.

```sh
git push origin master
```

## Uwagi Końcowe

Podczas scalania dwóch repozytoriów mogą wystąpić konflikty, które trzeba ręcznie rozwiązać. Przed rozpoczęciem procesu scalania upewnij się, że posiadasz najnowsze wersje obu repozytoriów i że wszyscy członkowie zespołu są świadomi tego procesu.

Jeśli pracujesz na innych gałęziach niż `master`, dostosuj komendy odpowiednio do swoich potrzeb.
