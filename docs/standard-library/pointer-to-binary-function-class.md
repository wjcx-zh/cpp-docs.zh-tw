---
title: "pointer_to_binary_function 類別 | Microsoft Docs"
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
  - "std::pointer_to_binary_function"
  - "xfunctional/std::pointer_to_binary_function"
  - "pointer_to_binary_function"
  - "std.pointer_to_binary_function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointer_to_binary_function 類別"
  - "pointer_to_binary_function 函式"
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointer_to_binary_function 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將二元函式指標轉換成適應性二元函式。  
  
## 語法  
  
```  
template<class Arg1, class Arg2, class Result>  
   class pointer_to_binary_function   
   : public binary_function <Arg1, Arg2, Result>   
   {  
   public:  
   explicit pointer_to_binary_function(  
      Result (*_pfunc )( Arg1, Arg2 )   
   );  
   Result operator()(  
      Arg1 _Left,   
      Arg2 _Right  
   ) const;  
   };  
```  
  
#### 參數  
 `_pfunc`  
 要轉換的二元函式。  
  
 `_Left`  
 左 *\*\_pfunc* 物件上呼叫。  
  
 `_Right`  
 正確的物件 *\*\_pfunc* 呼叫。  
  
## 傳回值  
 樣板類別儲存 **\_pfunc**複本。  它會定義成員的函式 `operator()` 為傳回\* \(**\_pfunc**\) \(\_Left， \_Right\)。  
  
## 備註  
 二元函式指標是函式物件，可以傳遞至預期二進位函式做為參數的所有標準樣板程式庫演算法，不過，它不是適應性。  若要將它與配置器，例如將值繫結至它或使用它與負元件，必須提供它以使這種符合可的巢狀型別 **first\_argument\_type**和 **second\_argument\_type**和 **result\_type** 。  由 `pointer_to_binary_function` 的允許轉換函式配接器與二元函式指標搭配使用。  
  
## 範例  
 直接很少使用 `pointer_to_binary_function` 建構函式。  提供的範例參閱 Helper 函式 [ptr\_fun](../Topic/ptr_fun%20Function.md) 宣告和使用 `pointer_to_binary_function` 配接器述詞。  
  
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [標準樣板程式庫](../misc/standard-template-library.md)