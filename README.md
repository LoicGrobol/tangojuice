# :beverage_box: TangoJuice
*Vocabulary extractor*

Language learning web app that extracts the vocabulary from a webpage or a video's captions, filters it by difficulty level and automatically creates Anki flashcards.

[Links and ideas on Notion](https://sturdy-starfish-3ee.notion.site/Projet-API-31a173f329eb45c4acdcfc5e60d851e1)

[Consignes](https://loicgrobol.github.io/web-interfaces/assignments/projets.html)

## How to run the API locally
* clone repo
* setup virtual environment:
    ```console
    python3 -m virtualenv .venv
    source .venv/bin/activate
    pip install -U -r requirements.txt
    ```
* start uvicorn 
    ```console
    uvicorn app:app
    ```
* go to [localhost:8000](http://localhost:8000)

## To-do list
- [ ] **PL** - Implémenter la **traduction** des mots et des phrases
    - [ ] Trouver une API pour les mots (Wikitonary?) https://en.wiktionary.org/w/api.php
    - [x] Test API PONS (mais qui ne marche pas du tout pour toutes les combinaisons de langues)
    - [ ] Pour les phrases, implémenter avec `googletrans` > super unreliable!
- [ ] **Améliorer l'extraction** `vocab.py` extraction du vocab à partir d'une string.
    - [ ] utiliser la fréquence du lemme
    - [ ] déterminer seuils de "rareté" et des mots à ignorer (trop communs)
    - [x] refaire les json de fréquence avec les vraies fréquences relatives
    - [x] ajouter fréquence par lemme (mais lemmatisation de la liste de mot via SpaCy, pas sûre de la qualité...)
    - [ ] Transcription en pinyin / romaji
    - [ ] si c'est pas kanji, ça dégage
- [ ] Create a database that holds the extracted words. Should we store it forever or empty it after a while?
- [ ]  S’occuper de l’interface HTML
    - [ ] Traduire interface en anglais
    - [ ] Mettre un peu de CSS pour que ça soit moins moche ?
    - [ ] Ajouter les options de langues à la page index. Pour la langue de traduction, automatiser. Astuce : `from googletrans import LANGUAGES`
    - [ ] Ajouter menu d'export qui se déplace avec le scroll
    - [ ] Intégrer nouvelles infos au tableau des résultats
    - [x] Copier les *tabs* de https://validator.w3.org/#validate_by_input
- [ ] créer flashcards Anki
    - [ ] sélection des mots
    - [x] création d'un fichier de flashcards
    - [ ] déplacer sur la la page de résultat
- [x] Ajouter possibilité d'envoyer un fichier srt dans l'API
- [x]  Script qui scrape un site et récupère le contenu texte, avec option « récursive »
- [x]  Ajouter support Youtube
- [x]  Faire l’API qui prend le lien  et renvoie un json
- [x] Ajouter un input text (pour extraire voc à partir d'un copier-coller)
- [ ] Vérifier que l’utilisateur a bien mis la bonne langue (lui demander de vérifier)
- [ ] Gérer la différence entre le chinois tradi (tw) et le chinois simplifié aka vérifier si spacy le fait


**Idées d’amélioration**

- [x]  Ne pas juste renvoyer des mots…
- [x]  Renvoyer les informations morphosyntaxiques (avec SpaCy)
- [ ]  Gestion des entités nommées
