---
tags:
    - Docker
    - Docker Desktop
    - Instalacja
    - Windows
    - FAQ
---

# Instalacja Docker Desktop w Windows 10 i 11

## Co potrzebuję, żeby zainstalować Docker Desktop?
Musisz mieć komputer z systemem Windows 10 lub 11. Ważne, żeby system był zaktualizowany – sprawdź to w ustawieniach w sekcji `Aktualizacje Windows`. Potrzebujesz też trochę miejsca na dysku (około 10 GB) i połączenia z internetem, żeby pobrać program.

## Skąd pobrać Docker Desktop?
Wejdź na oficjalną stronę Docker: ([www.docker.com](https://docker.com))  . Kliknij przycisk `Download Docker Desktop` – wybierz wersję dla Windows (najczęściej będzie to wersja AMD64). Plik się pobierze, a Ty musisz go potem otworzyć.

## Co zrobić, jeśli instalacja się nie zaczyna?
Sprawdź, czy pobrałeś cały plik – czasem internet przerywa i plik jest uszkodzony. Jeśli nic się nie dzieje po kliknięciu, upewnij się, że masz uprawnienia administratora. Kliknij prawym przyciskiem myszy na plik instalacyjny i wybierz `Uruchom jako administrator`.

## Problemy z WSL 2
**Problem:** Instalator informuje, że WSL 2 jest wymagane, a nie zostało znalezione.

**Co to jest WSL 2?** WSL 2 (Windows Subsystem for Linux wersja 2) to funkcja systemu Windows, która pozwala uruchamiać programy linuxowe w Windows. Docker potrzebuje tej funkcji, aby działać poprawnie.

**Rozwiązanie:**

1. Otwórz PowerShell jako administrator

        ![](./assets/docker_desktop__powershell.png)

2. Wpisz taką komendę i potwierdź je Enterem:

   ```powershell
   wsl --install -d Ubuntu-22.04
   ```
2. Zrestartuj komputer.
To automatycznie zainstaluje WSL 2 i jeśli Docker Desktop nie dokończy sam instalacji to należy go odinstalować i **zainstalować ponownie** od nowa (patrz punkt 6.).

## Ustawienie w BIOS Intel Virtualization Technology (VMX)

**Co to jest BIOS?** BIOS to specjalny program uruchamiany podczas startu komputera, zanim włączy się Windows. Pozwala na zmianę podstawowych ustawień sprzętowych komputera, takich jak włączenie funkcji wirtualizacji, która jest potrzebna dla Docker Desktop.

1. Wejdź do BIOS, podczas uruchamiania komputera naciskaj kilkukrotnie `F2` lub inny przycisk zależnie od producenta komputera

        ![](./assets/docker_desktop__bios.png)

2. Wybierz `Advanced`, następnie `CPU Configuration` lub `Configuration` w starszych komputerach, wyszukaj linijki `Intel Virtualization Technology (VMX)` i wybierz `Enabled`

3. Teraz musisz wyjść z BIOS zapisując zmiany. Czyli najpierw na górze strony przycisk `Exit`, a następnie `Save and Exit`

## Instalacja się zawiesza – co robić?
Spróbuj zamknąć inne programy, które mogą obciążać komputer, np. przeglądarkę z wieloma kartami. Jeśli to nie pomoże, to sprawdź w zainstalowanych aplikacjach Windows czy już częściowo Docker się nie zainstalował. Odinstaluj go, uruchom komputer ponownie i spróbuj jeszcze raz.

1. Otwórz panel Aplikacje:

        ![](./assets/docker_desktop__aplikacje.png)

2. Znajdź Docker Desktop, kliknij na `...` z prawej strony i wybierz `Odinstaluj`

        ![](./assets/docker_desktop__odinstaluj.png)

3. Zrestartuj komputer i zacznij proces instalacji od nowa.


## Wirtualizacja (Hyper-V/Windows Hypervisor Platform) jest wyłączona
**Problem:** Docker nie może uruchomić maszyn wirtualnych.
**Rozwiązanie:**

1. Wyszukaj w menu Start "Włącz lub wyłącz funkcje systemu Windows".

2. Zaznacz **Hyper-V** oraz **Windows Hypervisor Platform**.

3. Zrestartuj komputer.

To umożliwi Dockerowi korzystanie z wbudowanego hiperwizora Microsoftu.


## Konflikt z programem antywirusowym lub zaporą
**Problem:** Instalacja zatrzymuje się lub Docker nie startuje.
**Rozwiązanie:**

1. Tymczasowo wyłącz oprogramowanie zabezpieczające (np. Windows Defender, Avast).

2. Po instalacji dodaj Docker Desktop do wyjątków.


## Jak sprawdzić, czy Docker działa?
Po instalacji zobaczysz ikonkę Docker (mały wieloryb) na pasku zadań, obok zegarka. Kliknij ją – jeśli się otwiera i nie pokazuje błędów, to wszystko jest w porządku!

## 10. Docker Desktop nie uruchamia się po instalacji
**Problem:** Po zainstalowaniu nie pojawia się okno aplikacji.
**Rozwiązanie:**

1. Sprawdź w Menedżerze zadań `Ctrl + Alt + Del` wybierz `Procesy` w polu wyszukiwarki wpisz "docker" i sprwdź czy masz jakieś uruchomione procesy.

2. Mogą tam być uruchomine `Docker Desktop` lub `com.docker.backend`.

3. Zamknij je klikając prawym klawiszem myszy i wybierając `Zamknij zadanie`.

## Każdy problem
Naptkając jakikolwiek problem podczas instalacji lub działania Docker Desktop warto przestawić swój problem dla chata AI (Chat GPT, Cloude, Grok). Warto wtedy dodać, że nie jest się informatykiem i żeby odpowiedział prostym językiem, z opisaniem wszystkich potrzebnych kroków.
