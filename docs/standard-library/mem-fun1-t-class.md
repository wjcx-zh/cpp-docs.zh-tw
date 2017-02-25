---
title: "mem_fun1_t 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mem_fun1_t"
  - "std.mem_fun1_t"
  - "std::mem_fun1_t"
  - "xfunctional/std::mem_fun1_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun1_t 類別"
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# mem_fun1_t 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為一配接器類別，此類別允許 **non\_const** 成員函式在使用指標引數初始化時，接受單一引數並被呼叫為二元函式物件。  
  
## 語法  
  
```  
template<class Result, class Type, class Arg>  
   class mem_fun1_t : public binary_function<Type *, Arg, Result> {  
      explicit mem_fun1_t(  
         Result (Type::* _Pm )( Arg )   
         );  
      Result operator()(  
         Type* _Pleft,   
         Arg _Right  
         ) const;  
   };  
```  
  
#### 參數  
 `_Pm`  
 對類別要轉換的 \[**型別**\] 的成員函式的指標函式物件。  
  
 `_Pleft`  
 `_Pm` 物件成員函式呼叫。  
  
 `_Right`  
 提供給 `_Pm`的引數。  
  
## 傳回值  
 可調整的二元函式。  
  
## 備註  
 樣板類別中私用成員中的 `_Pm`複本，必須是指標到 \[**型別**\] 類別的成員函式。  它會定義成員的函式 `operator()` 為傳回 \(**\_Pleft**\)\>\* `_Pm`\) \(**\_Right**\)。  
  
## 範例  
 通常不會直接使用 `mem_fun1_t` 建構函式;Helper 函式 `mem_fun` 用來符合成員函式。  提供的範例參閱 [mem\_fun](../Topic/mem_fun%20Function.md) 使用成員函式配接器。  
  
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)