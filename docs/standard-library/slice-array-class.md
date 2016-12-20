---
title: "slice_array 類別 | Microsoft Docs"
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
  - "slice_array"
  - "valarray/std::slice_array"
  - "std.slice_array"
  - "std::slice_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "slice_array 類別"
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# slice_array 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

透過在子集陣列之間的作業支援立體物件的內部，其他的樣板類別由切割 valarray 定義。  
  
## 語法  
  
```  
template<class Type>  
   class slice_array : public slice {  
public:  
   typedef Type value_type;  
   void operator=(  
      const valarray<Type>& x  
   ) const;  
   void operator=(  
      const Type& x  
   ) const;  
   void operator*=(  
      const valarray<Type>& x  
   ) const;  
   void operator/=(  
      const valarray<Type>& x  
   ) const;  
   void operator%=(  
      const valarray<Type>& x  
   ) const;  
   void operator+=(  
      const valarray<Type>& x  
   ) const;  
   void operator-=(  
      const valarray<Type>& x  
   ) const;  
   void operator^=(  
      const valarray<Type>& x  
   ) const;  
   void operator&=(  
      const valarray<Type>& x  
   ) const;  
   void operator|=(  
      const valarray<Type>& x  
   ) const;  
   void operator<<=(  
      const valarray<Type>& x  
   ) const;  
   void operator>>=(  
      const valarray<Type>& x  
   ) const;  
// The rest is private or implementation defined  
}  
```  
  
## 備註  
 類別會描述與類別一起儲存類別 [valarray](../standard-library/valarray-class.md)**\<Type\>**物件的參考， [配量](../standard-library/slice-class.md)物件，描述項目序列 **valarray\<Type\>** 物件中選取的物件。  
  
 樣板類別由某些 valarray 作業直接在程式間接建置，因此無法使用。  切割註標運算子使用的內部，其他的樣板類別:  
  
 `slice_array`\<`valarray`\<\[**型別**\]\>\[**型別**\]::`operator[]` \(`slice`\)。  
  
 您可以撰寫表單 [VA &#91;&#93; sl](../Topic/valarray::operator.md)的運算式只建構 **slice\_array\<Type\>** 物件，預設的 **sl** valarray **va**。  slice\_array 類別的成員函式接著會與對應的函式簽章定義為 **valarray\<Type\>**，不過，選取的項目序列只會受到影響。  順序由 slice\_array 由預設建構函式、一個切割區段的第一個項目，數目的項目和項目之間距離的三個參數定義。  從 **va**宣告的 valarray **va** 的 slice\_array 剪下 \[`slice`\(2， 5， 3\)\] 選取與索引 2， 5， 8， 11 和 14 的元素從 **va**。  索引必須是有效才能程序可以有效。  
  
## 範例  
 中的 [slice::slice](../Topic/slice::slice.md) 參閱本範例說明如何宣告和使用 slice\_array。  
  
## 需求  
 **標頭：** \<valarray\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)