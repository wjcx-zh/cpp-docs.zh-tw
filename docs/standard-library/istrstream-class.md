---
title: "istrstream 類別 | Microsoft Docs"
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
  - "istrstream"
  - "std::istrstream"
  - "std.istrstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istrstream 類別"
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# istrstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明的物件可控制從 [strstreambuf](../standard-library/strstreambuf-class.md) 類別的資料流緩衝區中，擷取項目及編碼物件。  
  
## 語法  
  
```  
  
class istrstream : public istream  
  
```  
  
## 備註  
 此物件會儲存類別 `strstreambuf` 的物件。  
  
> [!NOTE]
>  這個類別已被取代。 請考慮使用 [istringstream](../Topic/istringstream.md) 或 [wistringstream](../Topic/wistringstream.md) 改。  
  
### 建構函式  
  
|||  
|-|-|  
|[istrstream](../Topic/istrstream::istrstream.md)|建構類型 `istrstream` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[rdbuf](../Topic/istrstream::rdbuf.md)|將指標傳回至資料流的相關 `strstreambuf` 物件。|  
|[str](../Topic/istrstream::str.md)|呼叫 [freeze](../Topic/strstreambuf::freeze.md)，然後將指標傳回至受控制序列的開頭。|  
  
## 需求  
 **標頭：**\<strstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [istream](../Topic/istream.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)