# [www.multiobjects.com](http://www.multiobjects.com)

## menu

+ [multiobjects.com](http://www.multiobjects.com)
+ [docs](http://docs.multiobjects.com)
+ [logo](http://logo.multiobjects.com)
+ [roadmap](http://roadmap.multiobjects.com)
+ [identity](http://identity.multiobjects.com)



## catalog of components
component = action + object
```bash
http://{catalog}.multiobjects.com/{component}.{extension}
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
        ReadContent(Message)
        ReceiveMessage(Message)
        SendMessage(Message)
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
