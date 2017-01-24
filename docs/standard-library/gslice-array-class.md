---
title: "gslice_array 類別 | Microsoft Docs"
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
  - "std::gslice_array"
  - "gslice_array"
  - "valarray/std::gslice_array"
  - "std.gslice_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gslice_array 類別"
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gslice_array 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援一般配量之內部，其他的樣板類別透過在一般切割定義的子集陣列之間的作業物件 valarray。  
  
## 語法  
  
```  
template<class Type>  
   class gslice_array : public gsplice {  
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
 類別與物件描述項目序列 **valarray\<Type\>** 物件中選取類別 [gslice](../standard-library/gslice-class.md) 的 **gs** 一起說明儲存物件類別 [valarray](../standard-library/valarray-class.md)**\<Type\>va** 的參考的物件。  
  
 您可以撰寫表單 [VA &#91;&#93; gs](../Topic/valarray::operator.md)的運算式只建構 **gslice\_array\<Type\>** 物件。  gslice\_array 類別的成員函式接著會與對應的函式簽章定義為 **valarray\<Type\>**，不過，選取的項目序列只會受到影響。  
  
 樣板類別由某些 valarray 作業直接在程式間接建置，因此無法使用。  切割註標運算子使用內部輔助樣板類別:  
  
 `gslice_array`\<`valarray`\<\[**型別**\]\>\[**型別**\]\>::**const** `operator[]` \(**gslice&**\)。  
  
 您可以撰寫表單 **va\[gsl\]**的運算式只建構 **gslice\_array\<Type\>** 物件，預設的 **gsl** valarray **va**。  gslice\_array 類別的成員函式接著會與對應的函式簽章定義為 **valarray\<Type\>**，不過，選取的項目序列只會受到影響。  順序由 gslice\_array 由預設建構函式、索引在第一個切割區段的第一個項目，數目的在每個切割的項目和項目之間距離的三個參數定義在每個切割。  
  
 在下列範例中：  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);  
// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 索引必須是有效才能程序可以有效。  
  
## 範例  
 中的 [gslice::gslice](../Topic/gslice::gslice.md) 參閱本範例說明如何宣告和使用 slice\_array。  
  
## 需求  
 **標頭：** \<valarray\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)