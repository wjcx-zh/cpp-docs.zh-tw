---
title: "&lt; &gt; streambuf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<streambuf>"
  - "<streambuf>"
  - "streambuf/std::<streambuf>"
  - "std.<streambuf>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "streambuf 標頭"
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt; &gt; streambuf
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 iostreams 標準標頭 \<streambuf\> 來定義範本類別 [basic\_streambuf](../standard-library/basic-streambuf-class.md)，這是 iostreams 類別作業的基礎。 此標頭通常會由其他 iostream 標頭所納入；您很少會需要直接將其納入。  
  
## 語法  
  
```  
  
#include <streambuf>  
  
```  
  
### Typedefs  
  
|||  
|-|-|  
|[streambuf](../Topic/streambuf.md)|會使用 `char` 做為範本參數的 `basic_streambuf` 特製化。|  
|[wstreambuf](../Topic/wstreambuf.md)|會使用 `wchar_t` 做為範本參數的 `basic_streambuf` 特製化。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_streambuf 類別](http://msdn.microsoft.com/zh-tw/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|此範本類別描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)