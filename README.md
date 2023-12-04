# [www.github.io](http://www.github.io)

+ [github.io](http://www.github.io)
+ [docs](http://docs.github.io)
+ [logo](http://logo.github.io)
+ [roadmap](http://roadmap.github.io)
+ [identity](http://identity.github.io)
+ [contribution](http://contribution.softreck.dev)




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

Sentence:
  - if I Receive Message then Send Message and Create Content text sentence: Thank You
    - Receive Message
    - Send Message
    - Create Content
        - text:
            - sentence: Thank You

```


#### 2. Relations

```yml
Exchange Message:  
  Send Message:
    Create Content
  Receive Message:
    Read Content
```



### Roles

#### 1. Relations

```yml
TeleCommunication:
  Provider:
    Sender:
      Creator
    Receiver:
      Reader
```


#### 2. Groups

```yml
Communicants:
  - Sender
  - Receiver

Correspondent:
  - Creator
  - Reader
```


#### 3. Layers


```yml
Provider:
  - Communicants
    - Correspondent
```







---

+ [issue](https://github.com/multiobjects/www/issues/new)
+ [edit](https://github.com/multiobjects/www/edit/main/README.md)
+ [git](https://github.com/multiobjects/)
