---
tags:
  - Workflow
  - Node
  - Local File Trigger 
---

# **Rozwiązania problemów z workflowami z lekcji**

## **Workflow z czytaniem lokalnych plików nie działa - Local Files Trigger nie reaguje**

1. Jeśli pracujesz na systemie Windows i masz podpięty prawidłowo volumen do folderu `pliki_n8n`, a Local Files Trigger nie reaguje
   ![](assets/workflows__local_files_example_1.png)

1. Kliknij dwukrotnie w node `Local File Trigger`
   ![](assets/workflows__local_files_example_2.png)

1. Kliknij w `Add Option`
   ![](assets/workflows__local_files_example_3.png)

1. Z listy wybierz `Use Polling`
   ![](assets/workflows__local_files_example_4.png)

1. Kliknij w suwak tak, żeby się zaświecił na zielono
   ![](assets/workflows__local_files_example_5.png)

1. Powtórz test przenosząc plik ze zdjęciem do folderu i teraz powinno działać
    <div class="video-wrapper">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/VNyzU-CtOAw?si=xKw39F_Wl0PNxz4-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>

1. Jeśli wciąż nie działa, **usuń kontener** i spróbuj ponownie.
   ![](assets/workflows__delete_container.png)
