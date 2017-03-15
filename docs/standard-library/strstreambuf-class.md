---
title: "strstreambuf 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.strstreambuf"
  - "strstreambuf"
  - "std::strstreambuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstreambuf 類別"
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# strstreambuf 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個資料流緩衝區，該緩衝區可控制儲存在 `char` 陣列物件中項目序列之間的項目傳輸。  
  
## 語法  
  
```  
  
class strstreambuf : public streambuf  
  
```  
  
## 備註  
 根據物件的建構方式，它可以視需要配置、擴充和釋出，以回應序列中的變更。  
  
 `strstreambuf` 類別的物件會將模式的幾個位元資訊儲存為其 `strstreambuf` 模式。 這些位元表示受控制的序列是否：  
  
-   已配置，且最後需要釋放。  
  
-   可修改。  
  
-   可透過重新配置儲存體來擴充。  
  
-   已凍結，因此需要解除凍結再終結物件，或由物件以外的代理程式釋放 \(如果已配置\)。  
  
 不論這些個別模式位元的狀態為何，您都無法修改或擴充凍結的受控制序列。  
  
 這個物件也會儲存控制 `strstreambuf` 配置的兩個函式指標。 如果這些指標是 null 指標，則該物件會規劃自己的方法來配置及釋放受控制序列的儲存體。  
  
> [!NOTE]
>  這個類別已被取代。 請考慮使用 [stringbuf](../Topic/stringbuf.md) 或 [wstringbuf](../Topic/wstringbuf.md) 改。  
  
### 建構函式  
  
|||  
|-|-|  
|[strstreambuf](../Topic/strstreambuf::strstreambuf.md)|建構類型 `strstreambuf` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[凍結](../Topic/strstreambuf::freeze.md)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|  
|[Overflow \- 溢位](../Topic/strstreambuf::overflow.md)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|  
|[pbackfail](../Topic/strstreambuf::pbackfail.md)|嘗試將項目放回輸入資料流，然後將其設為目前項目 \(由下一個指標指向\) 的受保護虛擬成員函式。|  
|[pcount](../Topic/strstreambuf::pcount.md)|傳回寫入至受控制序列的元素計數。|  
|[seekoff](../Topic/strstreambuf::seekoff.md)|受保護虛擬成員函式嘗試改變受控制資料流目前的位置。|  
|[seekpos](../Topic/strstreambuf::seekpos.md)|受保護虛擬成員函式嘗試改變受控制資料流目前的位置。|  
|[str](../Topic/strstreambuf::str.md)|呼叫 [freeze](../Topic/strstreambuf::freeze.md)，然後將指標傳回至受控制序列的開頭。|  
|[溢位](../Topic/strstreambuf::underflow.md)|要從輸入資料流擷取目前項目的受保護虛擬函式。|  
  
## 需求  
 **標頭：**\<strstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [streambuf](../Topic/streambuf.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)