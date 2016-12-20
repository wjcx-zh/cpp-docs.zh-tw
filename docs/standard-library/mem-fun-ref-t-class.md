---
title: "mem_fun_ref_t 類別 | Microsoft Docs"
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
  - "xfunctional/std::mem_fun_ref_t"
  - "mem_fun_ref_t"
  - "std.mem_fun_ref_t"
  - "std::mem_fun_ref_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun_ref_t 類別"
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mem_fun_ref_t 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為一配接器類別，此類別允許 **non\_const** 成員函式在使用參考引數初始化時，不接受引數即被呼叫為一元函式物件。  
  
## 語法  
  
```  
template<class Result, class Type>  
   class mem_fun_ref_t : public unary_function<Type, Result> {  
      explicit mem_fun_ref_t(  
         Result ( Type::*_Pm )( )   
      );  
      Result operator()( Type& _Left ) const;  
   };  
```  
  
#### 參數  
 `_Pm`  
 對類別要轉換的 \[**型別**\] 的成員函式的指標函式物件。  
  
 `_Left`  
 `_Pm` 物件成員函式呼叫。  
  
## 傳回值  
 可調整的一元的函式。  
  
## 備註  
 樣板類別中私用成員中的 `_Pm`複本，必須是指標到 \[**型別**\] 類別的成員函式。  它會定義成員的函式 `operator()` 為傳回 \(**\_Left**。\* `_Pm`\) \(\)。  
  
## 範例  
 通常不會直接使用 `mem_fun_ref_t` 建構函式;Helper 函式 `mem_fun_ref` 用來符合成員函式。  提供的範例參閱 [mem\_fun\_ref](../Topic/mem_fun_ref%20Function.md) 使用成員函式配接器。  
  
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)