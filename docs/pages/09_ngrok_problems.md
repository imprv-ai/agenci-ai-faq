---
tags:
  - Moduł 3
  - ngrok
  - docker
  - domena ngrok
  - ngrok resetuje
---

# **Rozwiązania problemów z ngrok**

## **Nie wiem jaką mam domenę w ngrok**

1. Żeby znaleźć naszą domenę ngrok należy zalogować się na stronę [ngrok](https://dashboard.ngrok.com/) i przejść do zakładki [domains](https://dashboard.ngrok.com/domains)
    ![](assets/problems__ngrok__domain_1.png)

## **Ngrok mi nie działa**
1. Po wejściu na domenę ngrok widzę następującą stronę
    ![](assets/problems__ngrok__domain_2.png)

1. W takiej sytuacji upewnij się, że masz uruchomiony kontener `ngrok` w Docker Desktop
1. Jeśli nie masz uruchomionego kontenera `ngrok`, to uruchom go, a następnie odśwież stronę

## **Kontener ngrok mi się uruchamia i potem się zatrzymuje (resetuje się) w Docker Desktop**
1. W takiej sytuacji sprawdź `logi` kontenera, czyli informacje, które raportuje podczas działania
1. Wpisz w terminalu `docker logs ngrok` i przeczytaj, czy ngrok zgłasza jakiś problem. Wklej ten komunikat do ChatGPT i postaraj się zrozumieć, co może być problemem. W razie trudności opisz problem na Discord i załącz logi

## **Uruchamiam ngrok i wyskakuje mi taki błąd - the container name "/ngrok" is already used**
![](assets/problems__ngrok__already_exists_1.png)

1. Błąd ten oznacza, że masz już uruchomiony kontener o nazwie `ngrok`
1. Żeby wyświetlić wszystkie kontenery otwórz Docker Desktop lub wpisz w terminal i potwierdź enterem:
```
docker ps -a
```
1. Żeby pozbyć się błędu usuń istniejący kontener ngrok. Możesz to zrobić komendą:
```
docker rm -f ngrok
```
1. Następnie, żeby uruchomić nowy kontener, wywołaj poniższą komendę w terminalu. Pamiętaj, żeby podmienić `TWOJ_TOKEN_AUTENTYKACYJNY_NGROK` i `TWOJA_DOMENA_W_NGROK`
```
docker run -it -d --name ngrok -p 4040:4040 -e NGROK_AUTHTOKEN=TWOJ_TOKEN_AUTENTYKACYJNY_NGROK ngrok/ngrok:latest http host.docker.internal:5678 --domain=TWOJA_DOMENA_W_NGROK
```
## **Uruchamiam ngrok i wyskakuje mi błąd - pojawiają się dziwne znaczki i minusy**
**Taki**
![](assets/problems__ngrok__bad_formatting.png)
**lub taki**
```
PS C:\Users\zminda> docker run -it -d --name ngrok \
>> -p 4040:4040 -e \
>> NGROK_AUTHTOKEN= 00000000000000000 \
>> ngrok/ngrok:latest \
>> http host.docker.internal:5678 \
>> --domain= lark-sdfsdfsd-snake.ngrok-free.app
>>
At line:6 char:3
+ --domain= lark-sdfsdsfds-snake.ngrok-free.app
+   ~
Missing expression after unary operator '--'.
At line:6 char:3
+ --domain= lark-sdfsdfsd-snake.ngrok-free.app
+   ~~~
Unexpected token 'domain=' in expression or statement.
    + CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : MissingExpressionAfterOperator
```

1. Zazwyczaj oznacza to błąd w formatowaniu komendy. Uruchom poniższą komendę pamiętając, żeby podmienić `TWOJ_TOKEN_AUTENTYKACYJNY_NGROK` i `TWOJA_DOMENA_W_NGROK`. **Nie dawaj spacji przed ani po znaku =**

```
docker run -it -d --name ngrok -p 4040:4040 -e NGROK_AUTHTOKEN=TWOJ_TOKEN_AUTENTYKACYJNY_NGROK ngrok/ngrok:latest http host.docker.internal:5678 --domain=TWOJA_DOMENA_W_NGROK
```

## Niepoprawny token autentykacyjny

1. Jeśli wyskakuje błąd `authentication failed: The authtoken you specified does not look like a proper ngrok tunnel authtoken` to oznacza, że token autentykacyjny jest niepoprawny.
![](assets/problems__ngrok__inproper_authtoken.jpg)

1. PAMIĘTAJ! Wpisz "goły" token autentykacyjny, bez ekstra spacji lub dodawania `<` lub `>`. Przykładowa instrukcja dla token `123secret123secret123secret123` oraz domeny `moj-dostepny-do-uzycia-w-ngrok.ngrok-free.app`:
```bash
docker run -it -d --name ngrok -p 4040:4040 -e NGROK_AUTHTOKEN=123secret123secret123secret123 ngrok/ngrok:latest http host.docker.internal:5678 --domain=moj-dostepny-do-uzycia-w-ngrok.ngrok-free.app
```
