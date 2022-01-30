# OOP-SOLID-Principle
在物件導向程式中，遵循SOLID這五項基本原則，可以幫助程式設計師寫出好維護、易擴充的程式架構：

### S: Single responsibility principle(SRP) 單一職責

所謂的單一職責是指一個類別只負責一件事情，阿文18歲生日那天取得汽車駕照，爸爸買一台車可以在天空上飛、在路上走、在水下游的車給他當生日禮物，是不是很酷的事情!?

可是阿文想開這台車，就必須要有機師職照、汽車駕照、潛水艇駕駛證照才能上路，如果哪天這台車故障了，可能要修飛機的技師、修汽車的技師、修潛艇的技師三種專業人員一起查看問題在哪邊才能排除故障。

如果一個類別負擔太多工作，就會像上面的超級汽車一樣，不論是使用上或是後續的維護工作都可能會帶來很大的困擾。要注意單一職責不是指一個類別裡面只有一個方法，在這邊，我們這台車責任是要可以在路上行駛，不過這不代表這台車只會擁有在路上行駛這個方法，實際上，行駛是由前進、後退、左轉、右轉、剎車等等基本功能組合而成的。

但從另外一個角度來看，又要注意功能被切的太細碎造成過度設計（over design）的情況，一台車雖然可以拆成方向盤、大燈、引擎、汽缸等等零件，每一個零件也都有不同的功能，但對汽車駕駛人來說，只要知道車子怎麼開就夠了，不需要去理解車子內部詳細的構造。對維修技師來說，了解細部零件的功能反而才是必要的，因此要怎麼規劃一個類別的責任，就要視實際的需求而定。如何定義一個類別（物件）的責任是一個很抽象也很難釐清的事情，我們在這邊只是略為簡介一下，這部分就先到這裡就好。 

### O: Open/close principle(OCP) 開放/封閉原則
物件導向程式設計最重要的開放（擴充）封閉（修改）原則。一套軟體應該要保留彈性，可以擴充新功能，但如果裡面程式碼的耦合度（Coupling）過高，新增功能時可能會影響舊功能，甚至會造成程式Bug，因此增新功能時就必須很小心仔細以原本正常程式碼被改壞了，另外高耦合的程式碼在有Bug需要維護修改也是同樣的麻煩。有鑑於此，舊程式碼應該是封閉修改的，或是某個舊功能需要調整，也不應該取影響到其他功能。

以阿文的車來說，我們在設計時就要針對車上不同的功能做模組化，例如說想將大燈改成又白又亮刺瞎別人的眼睛，汽車技師只要更換燈泡，不需也不能動到引擎的部分（引擎部分封閉修改）；或者今天要阿文要上山賞雪，可以直接在輪胎上綁上雪鏈（開放擴充），就可以在雪地上行走，不用整個輪胎換掉。開放/封閉原則就如同字面上的意思，開放新增功能，封閉修改其他不相關的功能。 
### L: Liskov substitution principle(LSP) Liskov替換
在一個系統中，子類別應該可以替換掉父類別而不會影響程式架構。
阿文要開車去外婆家，阿文家車庫裡面有很多台車，我們先看其中三台車，如下圖：  
![image](/assets/1.png)

car
阿文坐上的樂高車後，發現這是樂高積木組成的模型車，沒有引擎，根本不能上路!!!
這時候子類別樂高車並沒有辦法執行父類別car的路上跑功能，這種情況就不符合Liskov替換原則，子類別應該可以執行父類別想做的事情。 

### I: Interface Segregation Principle(ISP) 介面隔離
把不同功能的功能從介面中分離出來。

阿文表示，上次要去阿嬤家算是特殊的需求，我家的車最主要就是拿來佔車庫避免空間浪費， 然後輪流擺在庭院炫富用，樂高車也可以算是一台車，我們來看看阿文家的車庫：  
![image](/assets/2.png)  
這邊有一個小問題，發現了嗎?對阿文來說，車子不一定要有「路上跑」這個功能，阿文的樂高車是沒辦法在路上的跑的，這明顯違反了上一條LSP，因此我們必須修改車子的定義 ，大部分的車有「路上跑」功能，因此我們可以將這個功能分割到其他介面，分割後如下圖，如此一來我們就用介面隔離「路上跑」這個功能：  
![image](/assets/3.png)  

### D: Dependency Inversion Principle(DIP) 依賴反轉
定義：高階模組不應依賴低階模組，兩個都應該依賴在抽象概念上；抽象概念不依賴細節，而是細節依賴在抽象概念。
上面這段文字看起來很抽象，讓我來翻譯翻譯，意思就是「話不能說的太死，盡量講一些概念性的東西」。

阿文要在庭院要弄一個賞車派對，邀請函上面寫著「阿文誠摯邀請您來欣賞Ferrari Fx2020超級跑車」，因此這個派對就會被綁死在Fx2020超級跑車上面。如果當天阿文的爸爸開著這輛車去打網球，阿文在開趴那天就很糗很糗了。

為了避免這種事情發生，邀請函上面最好是寫著「阿文誠摯邀請您來參加派對並且欣賞超級跑車」，這樣一來就算當天阿文爸把Ferrari Fx2020開走了， 他只要另外拿出一台超級跑車就可以，雖然朋友們會有受騙的感覺，不過至少不會讓阿文當場丟盡面子。 

資料來源:https://skyyen999.gitbooks.io/-study-design-pattern-in-java/content/oodPrinciple.html
