---
title: "&lt; &gt; istream | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istream/std::<istream>"
  - "std.<istream>"
  - "<istream>"
  - "std::<istream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream 標頭"
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt; &gt; istream
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義範本類別 basic\_istream，以調解 iostreams 的擷取，並定義範本類別 basic\_iostream，以調解插入和擷取。 標頭也會定義相關的操作工具。 此標頭檔通常會由其他 iostreams 標頭為您納入；您很少需要直接將其納入。  
  
## 語法  
  
```  
  
#include <istream>  
  
```  
  
### Typedefs  
  
|||  
|-|-|  
|[iostream](../Topic/iostream.md)|`char` 的特殊化類型 `basic_iostream`。|  
|[istream](../Topic/istream.md)|`char` 的特殊化類型 `basic_istream`。|  
|[wiostream](../Topic/wiostream.md)|**wchar** 的特殊化類型 `basic_iostream`。|  
|[wistream](../Topic/wistream.md)|**wchar** 的特殊化類型 `basic_istream`。|  
  
### 操作工具  
  
|||  
|-|-|  
|[ws](../Topic/ws.md)|略過資料流中的空白字元。|  
|[swap](../Topic/%3Cistream%3E%20swap.md)|交換兩個資料流物件。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\>\>](../Topic/operator%3E%3E%20\(%3Cistream%3E\).md)|從資料流中擷取字元和字串。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_iostream](../standard-library/basic-iostream-class.md)|可執行輸入和輸出的資料流類別。|  
|[basic\_istream](../standard-library/basic-istream-class.md)|此範本類別所說明的物件，可控制如何從具有類型 **Elem** \(也稱為 [char\_type](../Topic/basic_ios::char_type.md)\) 之元素的資料流緩衝區擷取元素和編碼物件；該類型的字元特性由類別 **Tr** \(也稱為 [traits\_type](../Topic/basic_ios::traits_type.md)\) 所決定。|  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)