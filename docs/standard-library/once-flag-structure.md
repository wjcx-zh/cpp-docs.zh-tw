---
title: "once_flag 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::once_flag"
dev_langs: 
  - "C++"
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# once_flag 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 `struct` 用來與樣板函式 [call\_once](../Topic/call_once%20Function.md) 即使在執行之前多執行緒可確保的初始化程式碼只能呼叫一次，。  
  
## 語法  
  
```cpp  
struct once_flag  
{  
   constexpr once_flag() noexcept;  
   once_flag(const once_flag&);  
   once_flag& operator=(const once_flag&);  
};  
```  
  
## 備註  
 `once_flag` `struct` 只有一個預設建構函式。  
  
 `once_flag` 型別的物件可以建立，但是，無法複製。  
  
## 需求  
 **標題:** mutex  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)