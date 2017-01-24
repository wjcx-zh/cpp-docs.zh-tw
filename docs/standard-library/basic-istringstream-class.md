---
title: "basic_istringstream 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_istringstream"
  - "sstream/std::basic_istringstream"
  - "basic_istringstream"
  - "std.basic_istringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_istringstream 類別"
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_istringstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個物件，該物件可控制從 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 類別的資料流緩衝區中擷取項目和編碼物件。  
  
## 語法  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_istringstream : public basic_istream<Elem, Tr>  
```  
  
#### 參數  
 `Alloc`  
 配置器類別。  
  
 `Elem`  
 字串之基本項目的類型。  
  
 *Tr*  
 字元特性是在字串的基本項目上特製化。  
  
## 備註  
 此範本類別所描述的物件，可控制如何從具有類型 **Elem** 項目之 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 類別的資料流緩衝區擷取項目和編碼物件；其中該 Elem 類型的字元特性由類別 **Tr** 所決定，且其項目由類別 `Alloc` 的配置器所配置。  這個物件會儲存 basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\> 類別的物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_istringstream](../Topic/basic_istringstream::basic_istringstream.md)|建構類型 `basic_istringstream` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_istringstream::allocator_type.md)|此類型是樣板參數 `Alloc` 的同義字。|  
  
### 成員函式  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_istringstream::rdbuf.md)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>。|  
|[str](../Topic/basic_istringstream::str.md)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|  
|[交換](../Topic/basic_istringstream::swap.md)|用所提供物件的值交換這個 `basic_istringstream` 物件中的值。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_istringstream::operator=.md)|從物件參數將值指派給這個 `basic_istringstream` 物件。|  
  
## 需求  
 **標頭：**\<sstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)