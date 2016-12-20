---
title: "&lt;ostream&gt; | Microsoft Docs"
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
  - "std.<ostream>"
  - "<ostream>"
  - "ostream/std::<ostream>"
  - "std::<ostream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostream 標頭"
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
caps.latest.revision: 20
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;ostream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義樣板類別 [basic\_ostream](../standard-library/basic-ostream-class.md)，這會調解 iostreams 的插入作業。  這個標頭也會定義幾個相關的操作工具。  \(通常會由另一個 iostreams 標頭為您包含這個標頭。  您很少需要直接包含這個標頭。\)  
  
## 語法  
  
```  
  
#include <ostream>  
  
```  
  
### Typedefs  
  
|||  
|-|-|  
|[ostream](../Topic/ostream.md)|從根據 `char` 特製化的 `basic_ostream` 和根據 `char` 特製化的 `char_traits` 建立類型。|  
|[wostream](../Topic/wostream.md)|從根據 `wchar_t` 特製化的 `basic_ostream` 和根據 `wchar_t` 特製化的 `char_traits` 建立類型。|  
  
### 操作工具  
  
|||  
|-|-|  
|[endl](../Topic/endl.md)|結束一行並清除緩衝區。|  
|[結尾](../Topic/ends%20\(Standard%20C++%20Library\).md)|結束字串。|  
|[flush](../Topic/flush%20\(Standard%20C++%20Library\).md)|清除緩衝區。|  
||將左 `basic_ostream` 物件參數的值與右 `basic_ostream` 物件參數的值交換。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \<\<](../Topic/operator%3C%3C%20\(%3Costream%3E\).md)|將各種類型寫入資料流。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_ostream](../standard-library/basic-ostream-class.md)|這個樣板類別所描述的物件，可控制將項目和編碼物件插入資料流緩衝區中。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)