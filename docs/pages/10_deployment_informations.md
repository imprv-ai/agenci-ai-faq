---
tags:
  - Moduł 5
  - railway
  - wdrazanie
  - deployment
  - subskrypcja railway
---

# **Wdrażanie N8N na zdalnym serwerze – dodatkowe informacje**

## **Moja karta płatnicza została odrzucona – Railway Hobby Plan**

1. Aby zasubskrybować Railway Hobby Plan, **należy podpiąć kartę kredytową lub debetową.**  
Próba dodania karty przedpłaconej pre-paid (np. z portfela internetowego Skrill) skutkuje pobraniem 1 USD w celu autoryzacji, a następnie odrzuceniem karty. Pobrana kwota zostanie później zwrócona.
   
      ![](assets/deployment_informations__railway__hobby_plan.png)


## **Jak zmienić wersję n8n na Railway**
  <div style="padding:62.5% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/1094347117?h=6acbaeb4c9&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="Zmiana wersji komponentów na Railway"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

## **Jak zmienić hasło do n8n na Railway**
  Będzie nam potrzebna komenda `n8n user-management:reset`, którą znamy z poradnika [Resetowanie loginu i hasła do lokalnego n8n](./08_reset_password_n8n.md#resetowanie-loginu-i-hasła-do-lokalnego-n8n)
  
  <div style="padding:75% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/1097765709?h=83d65c8270&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="reset_hasla_n 8n_railway-2025-07-01_09.28.55"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

## **Zmienił się ekran startowy tworzenia nowego projektu w Railway**

Ostatnia aktualizacja Railway wprowadziła nowy wygląd ekranu „New Project”. Jeśli korzystasz z szablonu do uruchomienia `n8n` w Railway, teraz zobaczysz nieco inny układ kroków. Poniżej znajdziesz aktualny, poprawny przepływ z przykładami ekranów.

1. Na ekranie „New Project” wybierz opcję **Deploy a template**.
   ![](assets/railway__new_project__deploy_template.png)

1. Na liście szablonów wybierz pozycję **N8N (w/ workers)**.
   ![](assets/railway__template__n8n_workers.png)

1. Na widoku „Deploy N8N (W/ Workers)” pozostaw domyślne ustawienia usług (`Primary`, `Worker`, `Redis`, `Postgres`) i kliknij przycisk **Deploy** na dole strony.
   ![](assets/railway__deploy_n8n_with_workers__deploy_button.png)

Po wdrożeniu Railway utworzy projekt z czterema usługami. Dalej postępuj zgodnie z instrukcjami konfiguracji środowiska z kursu.