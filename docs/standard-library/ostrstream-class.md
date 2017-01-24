---
title: "ostrstream 類別 | Microsoft Docs"
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
  - "std.oststream"
  - "oststream"
  - "std::oststream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostrstream 類別"
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: 20
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ostrstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明會控制如何在類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中插入元素和編碼物件的物件。  
  
## 語法  
  
```  
  
class ostrstream : public ostream  
  
```  
  
## 備註  
 此物件會儲存類別 `strstreambuf` 的物件。  
  
> [!NOTE]
>  這個類別已被取代。  請考慮改用 [ostringstream](../Topic/ostringstream.md) 或 [wostringstream](../Topic/wostringstream.md)。  
  
### 建構函式  
  
|||  
|-|-|  
|[ostrstream](../Topic/ostrstream::ostrstream.md)|建構類型 `ostrstream` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[凍結](../Topic/ostrstream::freeze.md)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|  
|[pcount](../Topic/ostrstream::pcount.md)|傳回寫入至受控制序列的元素計數。|  
|[rdbuf](../Topic/ostrstream::rdbuf.md)|將指標傳回至資料流的相關 `strstreambuf` 物件。|  
|[str](../Topic/ostrstream::str.md)|呼叫 [freeze](../Topic/strstreambuf::freeze.md)，然後將指標傳回至受控制序列的開頭。|  
  
## 需求  
 **標頭：**\<strstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [ostream](../Topic/ostream.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)