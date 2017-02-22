---
title: "&lt;new&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<new>"
  - "<new>"
  - "std.<new>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "new 標頭"
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;new&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義數個類型和函式，對在程式控制下之儲存體控制配置和釋放。  它也會定義儲存體管理錯誤報告的元件。  
  
## 語法  
  
```  
  
#include <new>  
  
```  
  
## 備註  
 在這個標頭宣告的某些函式為可取代的。  此實作提供預設版本，會在本文件中描述其行為。  然而程式可能以相同簽章定義函式，藉此在連結時取代預設版本。  此取代版本必須符合本文件中描述的需求。  
  
### 物件  
  
|||  
|-|-|  
|[nothrow](../Topic/nothrow%20\(%3Cnew%3E\).md)|為 **new** 和 **delete** 之 `nothrow` 版本提供做為引數所使用的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[new\_handler](../Topic/new_handler.md)|類型，指向適合做為新的處理常式使用之函式。|  
  
### 函式  
  
|||  
|-|-|  
|[set\_new\_handler](../Topic/set_new_handler.md)|當嘗試配置記憶體發生新的錯誤時，安裝此時所呼叫的使用者函式。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md)|由 delete 陳述式呼叫的函式，藉此取消配置物件個體的儲存區。|  
|[operator delete&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md)|由 delete 陳述式呼叫的函式，藉此取消配置物件陣列的儲存區。|  
|[operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md)|由 new 陳述式呼叫的函式，藉此配置物件個體的儲存區。|  
|[operator new&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md)|由 new 陳述式呼叫的函式，藉此配置物件陣列的儲存區。|  
  
### 類別  
  
|||  
|-|-|  
|[bad\_alloc 類別](../standard-library/bad-alloc-class.md)|描述例外狀況擲回的類別，藉此表示配置要求失敗。|  
|[nothrow\_t Class](../standard-library/nothrow-t-structure.md)|該類別可做為 new 運算子的函式參數使用，藉此表示此函式應該要傳回 null 指標，報告配置失敗，而非擲回例外狀況。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)