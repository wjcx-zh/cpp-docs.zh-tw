---
title: "basic_stringstream 類別 | Microsoft Docs"
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
  - "std.basic_stringstream"
  - "basic_stringstream"
  - "std::basic_stringstream"
  - "sstream/std::basic_stringstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_stringstream 類別"
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_stringstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述會控制如何使用類別 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 的資料流緩衝區來插入及擷取項目和編碼物件的物件。  
  
## 語法  
  
```  
  
        template <  
   class Elem,   
   class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_stringstream : public basic_iostream<Elem, Tr>  
```  
  
#### 參數  
 `Alloc`  
 配置器類別。  
  
 `Elem`  
 字串之基本項目的類型。  
  
 *Tr*  
 字元特性是在字串的基本項目上特製化。  
  
## 備註  
 此範本類別所描述的物件，可控制如何使用具有類型 **Elem** 項目之 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**, **Tr**, `Alloc`\> 類別的資料流緩衝區插入和擷取項目和編碼物件；其中該 Elem 類型的字元特性由類別 **Tr** 所決定，且其項目由類別 `Alloc` 的配置器所配置。  這個物件會儲存 basic\_stringbuf\<**Elem**, **Tr**, `Alloc`\> 類別的物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_stringstream](../Topic/basic_stringstream::basic_stringstream.md)|建構類型 `basic_stringstream` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_stringstream::allocator_type.md)|此類型是樣板參數 `Alloc` 的同義字。|  
  
### 成員函式  
  
|||  
|-|-|  
|[rdbuf](../Topic/basic_stringstream::rdbuf.md)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`, `Alloc`\>。|  
|[str](../Topic/basic_stringstream::str.md)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|  
  
## 需求  
 **標頭：**\<sstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)