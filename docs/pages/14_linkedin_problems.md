# Rozwiązania problemów z połączeniem n8n z LinkedIn

## Problem: Niepoprawny `Redirect URL` przy tworzeniu poświadczeń (credentials)

Podczas próby połączenia n8n z Twoim kontem LinkedIn, możesz napotkać problem w kroku tworzenia poświadczeń (credentials). Pole `Redirect URL` wygenerowane przez n8n zaczyna się od `http://` zamiast wymaganego `https://`.

LinkedIn, podobnie jak wiele innych usług, wymaga bezpiecznego połączenia `https://` do autoryzacji. Błąd ten wynika z faktu, że Twój lokalny kontener n8n nie wie, jaki jest jego publiczny, dostępny z internetu adres.

!!! danger "Przykład problemu"
    Tutaj pojawi się zrzut ekranu pokazujący błąd - pole `Redirect URL` bez `https://`.

## Rozwiązanie: Ustawienie zmiennej `WEBHOOK_URL` w Dockerze

Aby n8n poprawnie generował linki zwrotne, musisz poinformować go o jego publicznym adresie URL, który otrzymujesz z usługi `ngrok`. Robi się to poprzez ustawienie zmiennej środowiskowej `WEBHOOK_URL` podczas tworzenia kontenera n8n w Docker Desktop.

Proces ten jest identyczny jak w przypadku konfiguracji n8n do pracy z Telegramem.

### Krok 1: Uruchom `ngrok`

Upewnij się, że masz uruchomiony `ngrok` i wskazuje on na port Twojego kontenera n8n (domyślnie `5678`). Skopiuj adres `https://...`, który wygenerował `ngrok`.

### Krok 2: Utwórz nowy kontener z `WEBHOOK_URL`

Poniższy film pokazuje, jak ustawić zmienną środowiskową `WEBHOOK_URL` w interfejsie graficznym Docker Desktop.

<div class="video-container">
<iframe width="100%" height="100%" src="https://www.loom.com/embed/b0fb4aa94f90493da164214e88ee1c07?sid=4e6c8351-4ddb-4020-90fa-87b5534cfd04" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>

!!! success "Przykład poprawnej konfiguracji"
    Tutaj pojawi się zrzut ekranu pokazujący, jak dodać zmienną `WEBHOOK_URL` w oknie "Run a new container" w Docker Desktop.

### Alternatywa: Użycie linii komend

Możesz również stworzyć kontener, używając terminala. Pamiętaj, aby podmienić `TWÓJ_ADRES_Z_NGROK` na adres skopiowany z `ngrok`.

```bash
docker run -d --name n8n-linkedin \
  -p 5678:5678 \
  -v ~/Desktop/n8n_data:/home/node/.n8n \
  -v ~/Desktop/n8n_kurs/n8n_files:/pliki_n8n \
  -e GENERIC_TIMEZONE="Europe/Warsaw" \
  -e TZ="Europe/Warsaw" \
  -e WEBHOOK_URL="https://TWÓJ_ADRES_Z_NGROK" \
  n8nio/n8n:latest
```

Po poprawnym skonfigurowaniu kontenera, n8n będzie już generować prawidłowy `Redirect URL` z `https://`, co pozwoli na pomyślne połączenie z LinkedIn.
