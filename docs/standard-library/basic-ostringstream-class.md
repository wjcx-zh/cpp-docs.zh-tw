---
title: "basic_ostringstream 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_ostringstream"
  - "std.basic_ostringstream"
  - "sstream/std::basic_ostringstream"
  - "std::basic_ostringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ostringstream 類別"
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# basic_ostringstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個物件，該物件可控制將項目和編碼物件插入 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 類別的資料流緩衝區中。  
  
## 語法  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_ostringstream : public basic_ostream<Elem, Tr>  
```  
  
#### 參數  
 `Alloc`  
 配置器類別。  
  
 `Elem`  
 字串之基本項目的類型。  
  
 *Tr*  
 字元特性是在字串的基本項目上特製化。  
  
## 備註  
 這個類別所描述的物件，可控制將項目和編碼物件插入資料流緩衝區中、具有 **Elem** 類型的項目、其字元特性是由 **Tr** 類別所決定，而且其項目是由 `Alloc` 類別的配置器所配置。  這個物件會儲存 basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\> 類別的物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_ostringstream](../Topic/basic_ostringstream::basic_ostringstream.md)|建構類型 `basic_ostringstream` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_ostringstream::allocator_type.md)|此類型是樣板參數 `Alloc` 的同義字。|  
  
### 成員函式  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_ostringstream::rdbuf.md)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>。|  
|[str](../Topic/basic_ostringstream::str.md)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|  
  
## 需求  
 **標頭：**\<sstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)