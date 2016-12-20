---
title: "strstream 類別 | Microsoft Docs"
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
  - "std::strstream"
  - "strstream"
  - "std.strstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstream 類別"
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: 21
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述會控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取項目和編碼物件的物件。  
  
## 語法  
  
```  
  
class strstream : public iostream  
  
```  
  
## 備註  
 此物件會儲存類別 `strstreambuf` 的物件。  
  
> [!NOTE]
>  這個類別已被取代。  請考慮改用 [stringstream](../Topic/stringstream.md) 或 [wstringstream](../Topic/wstringstream.md)。  
  
### 建構函式  
  
|||  
|-|-|  
|[strstream](../Topic/strstream::strstream.md)|建構類型 `strstream` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[凍結](../Topic/strstream::freeze.md)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|  
|[pcount](../Topic/strstream::pcount.md)|傳回寫入至受控制序列的元素計數。|  
|[rdbuf](../Topic/strstream::rdbuf.md)|將指標傳回至資料流的相關 `strstreambuf` 物件。|  
|[str](../Topic/strstream::str.md)|呼叫 [freeze](../Topic/strstreambuf::freeze.md)，然後將指標傳回至受控制序列的開頭。|  
  
## 需求  
 **標頭：**\<strstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [iostream](../Topic/iostream.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)