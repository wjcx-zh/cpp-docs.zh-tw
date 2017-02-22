---
title: "basic_streambuf 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_streambuf"
  - "streambuf/std::basic_streambuf"
  - "std.basic_streambuf"
  - "std::basic_streambuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_streambuf 類別"
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# basic_streambuf 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。  
  
## 語法  
  
```  
template<class Elem, class Tr = char_traits<Elem> >  
   class basic_streambuf;  
```  
  
#### 參數  
 `Elem`  
 [char\_type](../Topic/basic_streambuf::char_type.md)。  
  
 `Tr`  
 字元 [traits\_type](../Topic/basic_streambuf::traits_type.md)。  
  
## 備註  
 此範本類別描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。  `basic_streambuf` 類別的物件協助以 `Tr` 類型的項目控制資料流，此類型也稱為 [char\_type](../Topic/basic_streambuf::char_type.md)，其字元特性由類別 [char\_traits](../standard-library/char-traits-struct.md) 決定，也稱為 [traits\_type](../Topic/basic_streambuf::traits_type.md)。  
  
 每個資料流緩衝區在概念上會控制兩個獨立的資料流：一個用於擷取 \(輸入\)，一個用於插入 \(輸出\)。  不過，特定的表示法可能使這些資料流之一或兩者無法存取。  它通常會維護兩個資料流之間的某種關聯性。  例如，您插入 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`\> 物件輸出資料流的內容，即是您稍後從其輸入資料流擷取的內容。  當您定位 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem` `Tr`\> 物件的一個資料流時，您會串聯地定位其他資料流。  
  
 範本類別 `basic_streambuf` 的公用介面提供通用於所有資料流緩衝區的作業，不過是經過特製化。  受保護的介面會提供資料流的特定表示法以執行其工作所需的作業。  受保護的虛擬成員函式可讓您針對資料流的特定表示法量身訂做衍生之資料流緩衝區的行為。  此程式庫中每個衍生的資料流緩衝區會描述其特製化受保護之虛擬成員函式行為的方式。  本主題描述基底類別的預設行為，這通常是不執行任何動作。  
  
 剩餘的受保護成員函式會控制要提供給資料流往返傳輸之任何儲存體之間的複製。  例如，輸入緩衝區的特性有：  
  
-   [eback](../Topic/basic_streambuf::eback.md)，緩衝區開頭的指標。  
  
-   [gptr](../Topic/basic_streambuf::gptr.md)，下個待讀取項目的指標。  
  
-   [egptr](../Topic/basic_streambuf::egptr.md)，剛好超過緩衝區結尾的指標。  
  
 同樣地，輸出緩衝區的特性有：  
  
-   [pbase](../Topic/basic_streambuf::pbase.md)，緩衝區開頭的指標。  
  
-   [pptr](../Topic/basic_streambuf::pptr.md)，下個待寫入項目的指標。  
  
-   [epptr](../Topic/basic_streambuf::epptr.md)，剛好超過緩衝區結尾的指標。  
  
 針對任何緩衝區，會使用下列通訊協定：  
  
-   如果下一個指標為 null，則沒有緩衝區存在。  否則，所有三個指標都指向相同的順序。  它們可以安全地比較順序。  
  
-   針對輸出緩衝區，如果下一個指標比較起來會小於結尾指標，您可以將項目儲存在下個指標所指定的寫入位置。  
  
-   針對輸入緩衝區，如果下一個指標比較起來會小於結尾指標，您可以在下個指標所指定的讀取位置讀取項目。  
  
-   針對輸入緩衝區，如果開始指標比較起來會小於下個指標，您可以將項目放回遞減過之下個指標所指定的放回位置。  
  
 您針對衍生自 `basic_streambuf`\<`Elem`, `Tr`\> 的類別所撰寫的任何受保護虛擬成員函式，都必須相互合作以維護這個通訊協定。  
  
 類別 `basic_streambuf`\<`Elem`, `Tr`\> 的物件會儲存先前所述的六個指標。  它也會在 [locale](../standard-library/locale-class.md) 類型的物件中儲存地區設定物件，以供衍生的資料流緩衝區使用。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_streambuf](../Topic/basic_streambuf::basic_streambuf.md)|建構類型 `basic_streambuf` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_streambuf::char_type.md)|將類型名稱與 `Elem` 樣板參數產生關聯。|  
|[int\_type](../Topic/basic_streambuf::int_type.md)|將  `basic_streambuf` 範圍內的類型名稱與 `Elem` 範本參數產生關聯。|  
|[off\_type](../Topic/basic_streambuf::off_type.md)|將  `basic_streambuf` 範圍內的類型名稱與 `Elem` 範本參數產生關聯。|  
|[pos\_type](../Topic/basic_streambuf::pos_type.md)|將  `basic_streambuf` 範圍內的類型名稱與 `Elem` 範本參數產生關聯。|  
|[traits\_type](../Topic/basic_streambuf::traits_type.md)|將類型名稱與 `Tr` 樣板參數產生關聯。|  
  
### 成員函式  
  
|||  
|-|-|  
|[eback](../Topic/basic_streambuf::eback.md)|受保護的函式，會傳回輸入緩衝區開頭的指標。|  
|[egptr](../Topic/basic_streambuf::egptr.md)|受保護的函式，會傳回剛好超過輸入緩衝區結尾的指標。|  
|[epptr](../Topic/basic_streambuf::epptr.md)|受保護的函式，會傳回剛好超過輸出緩衝區結尾的指標。|  
|[gbump](../Topic/basic_streambuf::gbump.md)|受保護的函式，會對輸入緩衝區的下個指標加上 `_Count`。|  
|[getloc](../Topic/basic_streambuf::getloc.md)|取得 `basic_streambuf` 物件的地區設定。|  
|[gptr](../Topic/basic_streambuf::gptr.md)|受保護的函式，會傳回輸入緩衝區下個項目的指標。|  
|[imbue](../Topic/basic_streambuf::imbue.md)|受保護的虛擬函式，由 [pubimbue](../Topic/basic_streambuf::pubimbue.md) 呼叫。|  
|[in\_avail](../Topic/basic_streambuf::in_avail.md)|傳回可以從緩衝區讀取的項目數。|  
|[Overflow \- 溢位](../Topic/basic_streambuf::overflow.md)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|  
|[pbackfail](../Topic/basic_streambuf::pbackfail.md)|受保護的虛擬成員函式，會嘗試將項目放回輸入資料流，然後將其設成目前的項目 \(由下一個指標指向\)。|  
|[pbase](../Topic/basic_streambuf::pbase.md)|受保護的函式，會傳回輸出緩衝區開頭的指標。|  
|[pbump](../Topic/basic_streambuf::pbump.md)|受保護的函式，會對輸出緩衝區的下個指標加上 `count`。|  
|[pptr](../Topic/basic_streambuf::pptr.md)|受保護的函式，會傳回輸出緩衝區下個項目的指標。|  
|[pubimbue](../Topic/basic_streambuf::pubimbue.md)|設定 `basic_streambuf` 物件的地區設定。|  
|[pubseekoff](../Topic/basic_streambuf::pubseekoff.md)|呼叫 [seekoff](../Topic/basic_streambuf::seekoff.md)，這是在衍生類別中遭覆寫的受保護虛擬函式。|  
|[pubseekpos](../Topic/basic_streambuf::pubseekpos.md)|呼叫 [seekpos](../Topic/basic_streambuf::seekpos.md)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且重設目前的指標位置。|  
|[pubsetbuf](../Topic/basic_streambuf::pubsetbuf.md)|呼叫 [setbuf](../Topic/basic_streambuf::setbuf.md)，這是在衍生類別中遭覆寫的受保護虛擬函式。|  
|[pubsync](../Topic/basic_streambuf::pubsync.md)|呼叫 [sync](../Topic/basic_streambuf::sync.md)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且更新這個緩衝區相關聯的外部資料流。|  
|[sbumpc](../Topic/basic_streambuf::sbumpc.md)|讀取並傳回目前項目，同時移動資料流指標。|  
|[seekoff](../Topic/basic_streambuf::seekoff.md)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[seekpos](../Topic/basic_streambuf::seekpos.md)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[setbuf](../Topic/basic_streambuf::setbuf.md)|受保護的虛擬成員函式會執行每個衍生資料流緩衝區的特定作業。|  
|[setg](../Topic/basic_streambuf::setg.md)|受保護的函式，會在開頭指標儲存 `_Gbeg`，在下個指標儲存 `_Gnext`，以及在輸入緩衝區的結尾指標儲存 `_Gend`。|  
|[setp](../Topic/basic_streambuf::setp.md)|受保護的函式，會在開頭指標儲存 `_Pbeg`，以及在輸出緩衝區的結尾指標儲存 `_Pend`。|  
|[sgetc](../Topic/basic_streambuf::sgetc.md)|傳回目前的項目而不變更資料流中的位置。|  
|[sgetn](../Topic/basic_streambuf::sgetn.md)|傳回讀取的項目數目。|  
|[showmanyc](../Topic/basic_streambuf::showmanyc.md)|受保護的虛擬成員函式，會傳回可從輸入資料流擷取的字元數計數，並確保程式不會無限地等候。|  
|[snextc](../Topic/basic_streambuf::snextc.md)|讀取目前項目並傳回下個項目。|  
|[sputbackc](../Topic/basic_streambuf::sputbackc.md)|將 `char_type` 放入資料流。|  
|[sputc](../Topic/basic_streambuf::sputc.md)|將字元放入資料流。|  
|[sputn](../Topic/basic_streambuf::sputn.md)|將字元字串放入資料流。|  
|[stossc](../Topic/basic_streambuf::stossc.md)|移動超過資料流中目前的項目。|  
|[sungetc](../Topic/basic_streambuf::sungetc.md)|從資料流取得字元。|  
|[交換](../Topic/basic_streambuf::swap.md)|用這個物件中的值，交換所提供之 `basic_streambuf` 物件參數中的值。|  
|[sync](../Topic/basic_streambuf::sync.md)|受保護的虛擬函式，會嘗試與任何相關聯的外部資料流同步處理控制資料流。|  
|[uflow](../Topic/basic_streambuf::uflow.md)|受保護的虛擬函式，會從輸入資料流擷取目前的項目。|  
|[溢位](../Topic/basic_streambuf::underflow.md)|受保護的虛擬函式，會從輸入資料流擷取目前的項目。|  
|[xsgetn](../Topic/basic_streambuf::xsgetn.md)|受保護的虛擬函式，會從輸入資料流擷取項目。|  
|[xsputn](../Topic/basic_streambuf::xsputn.md)|受保護的虛擬函式，會將項目插入輸出資料流。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_streambuf::operator=.md)|從另一個 `basic_streambuf` 物件指派這個物件的值。|  
  
## 需求  
 **標頭：**\<streambuf\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)