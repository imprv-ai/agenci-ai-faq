---
tags:
  - Moduł 3
  - Telegram 
  - Workflow
---

# **Rozwiązania problemów z połączeniem n8n z Telegramem**

## **Połączenie workflow z botem w Telegramie nie działa**

1. Na stronie Telegrama w adresie www przeglądarki jest numer, który potrzebujemy jako Chat ID.
   ![](assets/workflows__telegram_1.png)
1. Są przypadki, że ten numer nie ma na początku `-100`. Wtedy do skopiowanego numeru należy taki początek dodać ręcznie. 
   ![](assets/workflows__telegram_2.png)
   
## **Trigger do nasłuchiwania na wiadomości z Telegrama zgłasza błąd**

1. Uruchamiam workflow, w którym mam node nasłuchujący na Telegram i mam taki błąd
   ![](assets/workflow__telegram__webhook.png)

1. Należy ustawić zmienną środowiskową `WEBHOOK_URL` i jej wartość ustawić na domenę, którą mamy z `ngrok`

   ### WAŻNE! : wartość którą wpisujemy powinna mieć postać `https://TWOJA_DOMENA_NGROK`
   <div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/b0fb4aa94f90493da164214e88ee1c07?sid=e86d29a8-2a97-4b11-840f-2bea0575d1a5" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

## **Przesyłanie zdjęcia przez Telegram do agenta nie działa. Zatrzymuje się na node SWITCH**

1. Kiedy wysyłam zdjęcie, node SWITCH pokazuje taki problem
   ![](assets/workflow__telegram__photo_1.png)

1. Zwróć uwagę, żeby w `Routing Rules` w typie porównania wybrać `Array`, a następnie `exists`
   ![](assets/workflow__telegram__photo_2.png)
   ![](assets/workflow__telegram__photo_3.png)