# [www.multiobjects.com](http://www.multiobjects.com)

## menu

+ [multiobjects.com](http://www.multiobjects.com)
+ [docs](http://docs.multiobjects.com)
+ [logo](http://logo.multiobjects.com)
+ [roadmap](http://roadmap.multiobjects.com)
+ [identity](http://identity.multiobjects.com)



zbierac dane z różnych API zamieniać na CSV i czytać za pomocą SQL query - plainQuery, by móc np. czytać hurtowo moje repozytoria i poprawiać kod, opis w newralgicznych miejscach, aktualizować np. nieaktualne linki

do wykonywania/zapisywania danych trzeba by stworzyć view jako zbiorcze parametryzowane zadania dla wielu róznych API

a sam SQL można potem zastąpić warstwą text to sql i w ten sposób uzyskać łatwy dostęp do danych za pseudo czata - [edi.chat]

+ wystarczy CSV + adapter/driver
+ CSV można generować z bash-a/python-a

## TODO:


+ catalog z lista przykładowych funkcji i obiektów
 + GET http://catalog.multiobjects.com/component/{name}.{language}
 + GET http://catalog.multiobjects.com/object/{name}.{language}
  
### Funkcje:
+ plik python z listą przykładowych nazw komponentów w komentarzach
+ generator kodu na podstawie komentarzy
  
### Zdania:
+ zdanie
+ pętla ładowania ze zdania
  + rozbijanie na wyrażenia
  + pobieranie pliku yaml i ładowanie obiektów IN -> OUT
  + uruchamianie i zapisywanie do kolejki QUEUE
  + podawanie obiektu na wyjściu i wyjściu
  + skrypt python dla komend uruchamianych w konsoli z przykłądowymi zdaniami
  + testy IN/OUT
     
+ plik python z listą zdań w komentarzach
+ generator kodu na podstawie zdań
+ rozpoznawanie gramatyki i zamiana w jednym ciągu z jednego typy danych na drugi
+ QUEUE - array


## Concept:

```bash 
Public Network -> Private Network -> Component
Paragraph -> Sentence -> Part
```

- A paragraph is a public **network**
- A sentence is a private **network**
- A part of a sentence is a **component**




## Catalog of components

+ [multiobjects/catalog: catalog.multiobjects.com](https://github.com/multiobjects/catalog)

component = action + object
```bash
POST http://catalog.multiobjects.com/component/{component}.{language}
POST http://catalog.multiobjects.com/object/{component}.{language}
GET http://sentence.multiobjects.com/{sentence}
```

katalog sklada sie z nazw folderów w ktorych sa pliki: dokumentacji, kodu w roznych jezykach

pliki luzno w projekcie folderu:


### Actions

### Objects

### Components

### language:
- yaml
- python
- markdown
- bash

### Generowanie projektu z kodem w folderze
statyczy zbiór + JS aplikacja z zamianą nazw funkcji bez spacji
+ wybór maszyny na ktorej bedzie uruchamiana aplikacja, testowo docker
+ obieranie pliku funkcji lokalnie do folderu
+ import wszystkich funkcji do glownego programu
+ uruchomienie wedle kolejnosci
+ zwrocenie danych w oczekiwanym formacie
 
### Generowanie pliku kodu
generowanie z komentarzy python + markdown

```python
# catalogi:
# [import](http://sentence.multiobjects.com/{sentence})
# [import](http://catalog.multigit.com/{component})

logika FROM-TO: FROM: WriteContent TO: Print Content On Screen

# Sentence: WriteContent ....

# WriteContent
## ConvertContentToMessage
## SendMessage
### SelectReceiver
### ConnectToNetwork

# Sentence: Print Content On Screen ....

# Print Content On Screen
## ConnectToNetwork
## ReceiveMessage
## ReadMessage
## ConvertMessageToContent
## PrintContentOnScreen


```

## Deployment

- stworzenie pliku yaml ze zdaniem
- załączenie do klasy multiobjects(catalog_url)
- uruchomienie zadania multiobjects.sentence(sentence_yaml)
- uruchomienie zadania multiobjects.deploy(server)

zasada działania jak w apiDSL tylko z użyciem obiektów
streamowanie danych pomiędzy obiektami 


{catalog}
```
ExchangeMessage(Message):
    PrintOnScreen(Content)
        ReadContentFromMessage(Message)
        ReceiveMessage(Message)
        SendMessage(Message)
```
        
Zamiana zdania na funkcje


```python
# Print Content
def PrintContent(Content):

```                
        

rekurencja od ostatniego do pierwszego w zdaniu


## Server

```yaml
Server:
    pass:
    username:

```

## Sentence

```yaml
Sentence:
  - if I Receive Message then Send Message and Create Content text sentence: Thank You
    - Receive Message
    - Send Message
    - Create Content
        - text:
            - sentence: Thank You
```


        
## Catalog

```yaml
Components:  
    "Exchange Message":      # goal
      ROLE: Provider
      ACTION: Exchange     # verb/object
      OBJECT: Message      # object
    Send Message:          # goal
      ROLE: Sender
      ACTION: Send         # verb/object
      OBJECT: Message      # object
    Receive Message:       # object interface
      ROLE: Recipient
      ACTION: Receive      # verb/object
      OBJECT: Message      # object
    Create Content:        # object interface
      ROLE: Creator
      ACTION: Create       # verb/object
      OBJECT: Content      # object
    Read Content:          # object interface
      ROLE: Reader
      ACTION: Read         # verb/object
      OBJECT: Content      # object
    Convert Message To Content:    
      ROLE: Converter
      ACTION: Convert      # verb/object
      OBJECTS:
        IN: Message        # object
        OUT: Content       # object
    Create Sentence:        # object interface
      ROLE: Creator
      ACTION: Create       # verb/object
      OBJECT: Sentence      # object

Objects:
    Network:          
      - connect
      - disconnect        

    Provider:          
      - online
      - offline        
    
    Content:
      - create
      - read
      - delete
      - update
    
    Message:        
      - send
      - receive


Structure:
    Communicants:
        - Message
    Correspondent:
        - Content

    Content:
      - text
        - sentence
          - verb
          - object
      - image
        - picture
        - mimetype
          - svg
          - png
      - video

    
Actions:
  - send
  - receive
  - create
  - read
  - delete
  - update

```


### Relations

```yml
Exchange Message:  
  Send Message:
    Create Content
  Receive Message:
    Read Content
```



### Roles

```yml
TeleCommunication:
  Provider:
    Sender:
      Creator
    Receiver:
      Reader
```


### Groups

```yml
Communicants:
  - Sender
  - Receiver

Correspondent:
  - Creator
  - Reader
```


### Layers


```yml
Provider:
  - Communicants
    - Correspondent
```







## [contribution](http://contribution.softreck.dev)

+ [issue](https://github.com/multiobjects/www/issues/new)
+ [edit](https://github.com/multiobjects/www/edit/main/README.md)
+ [git](https://github.com/multiobjects/)
