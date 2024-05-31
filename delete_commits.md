# Instrukcja usuwania commitów po konkretnym wybranym commit w GIT

## Wstęp

Poniższa instrukcja opisuje krok po kroku, jak usunąć commity, które zostały zrobione po konkretnym wybranym commicie w systemie kontroli wersji Git. Przykładowo, jeśli chcemy usunąć commity, które zostały wykonane po commicie o identyfikatorze `abcd1234`, będziemy korzystać z komendy `git reset`.

## Kroki

1. **Zidentyfikuj commit, do którego chcesz wrócić:**

    Aby zidentyfikować identyfikator (hash) commita, do którego chcesz wrócić, możesz użyć komendy:

    ```sh
    git log
    ```

    Zobaczysz historie commitów w swoim repozytorium. Skopiuj identyfikator commita, do którego chcesz wrócić.

2. **Zapisz zmiany robocze:**

    Jeśli masz niezatwierdzone zmiany w swoim repozytorium, zapisz je przed wykonaniem resetu. Możesz je zapisać na stash:

    ```sh
    git stash save "Twoje zmiany"
    ```

3. **Wykonaj reset do wybranego commita:**

    Użyj komendy `git reset` z opcją `--hard`, aby zresetować bieżące gałęzie do wybranego commita. To usunie wszystkie commity wykonane po tym commicie:

    ```sh
    git reset --hard <commit-hash>
    ```

    Przykładowo, jeśli identyfikator commita to `abcd1234`, komenda będzie wyglądała tak:

    ```sh
    git reset --hard abcd1234
    ```

4. **Forcowane wypchanie zmian do zdalnego repozytorium:**

    Jeżeli chcesz, aby zmiany te były odzwierciedlone w zdalnym repozytorium, musisz użyć komendy `git push` z opcją `--force` (lub `-f`). **Uwaga:** To wymusi przepchnięcie Twoich zmian i może prowadzić do problemów dla innych współpracowników, więc upewnij się, że jesteś tego świadomy i przygotowany.

    ```sh
    git push origin <nazwa-gałęzi> --force
    ```

    Przykładowo, jeśli pracujesz na gałęzi `main`, komenda będzie wyglądała tak:

    ```sh
    git push origin main --force
    ```

5. **Przywróć zmiany ze stash (jeśli dotyczy):**

    Jeżeli zapisałeś swoje zmiany na stash w kroku drugim, przywróć je:

    ```sh
    git stash pop
    ```

## Uwagi Końcowe

Resetowanie git z opcją `--hard` oraz wymuszanie push (`--force`) mogą być działaniami destrukcyjnymi i powinny być wykonywane z ostrożnością. Przed podjęciem takiego działania, zwłaszcza w przypadku zdalnych repozytoriów współdzielonych z innymi, upewnij się, że wszyscy współpracownicy są świadomi tych zmian i że masz backup niezbędnych danych.

W przypadku jakichkolwiek wątpliwości skonsultuj się z zespołem przed wykonaniem resetu.

## Przydatne Źródła

- [Oficjalna dokumentacja Git](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book/en/v2) - darmowa książka dostępna online
