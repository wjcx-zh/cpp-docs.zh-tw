---
title: "allocator&lt;void&gt; 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::allocator<void>"
  - "std::allocator<void>"
  - "std.allocator<void>"
  - "allocator<void>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator<void> 類別"
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# allocator&lt;void&gt; 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`void`型別的樣板類別配置器的特製化，定義在此內容中有意義的型別。  
  
## 語法  
  
```  
template<>  
   class allocator<void> {  
   typedef void *pointer;  
   typedef const void *const_pointer;  
   typedef void value_type;  
   template<class Other>  
      struct rebind;  
   allocator( );  
   allocator(  
      const allocator<void>&  
   );  
   template<class Other>  
      allocator(  
         const allocator<Other>&  
      );  
   template<class Other>  
      allocator<void>& operator=(  
         const allocator<Other>&  
      );  
   };  
```  
  
## 備註  
 類別明確地特製化型別 void 樣板類別 [配置器](../standard-library/allocator-class.md)*。*其建構函式和指派運算子產生相同的行為像樣板類別的，不過，它會定義只有下列型別:  
  
-   [const\_pointer](../Topic/allocator::const_pointer.md)。  
  
-   [指標](../Topic/allocator::pointer.md)。  
  
-   [value\_type](../Topic/allocator::value_type.md)。  
  
-   [重新繫結](../Topic/allocator::rebind.md)，巢狀樣板類別。  
  
## 需求  
 **Header:** \<記憶體\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)