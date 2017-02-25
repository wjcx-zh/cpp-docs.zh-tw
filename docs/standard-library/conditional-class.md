---
title: "conditional 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::conditional"
  - "std.tr1.conditional"
  - "conditional"
  - "std.conditional"
  - "std::conditional"
  - "type_traits/std::conditional"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conditional 類別 [TR1]"
  - "conditional"
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# conditional 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據指定的條件選取這兩種類型之一。  
  
## 語法  
  
```  
template <bool B, class T1, class T2>  
    struct conditional;  
  
template <bool _Test, class _T1, class _T2>  
    using conditional_t = typename conditional<_Test, _T1, _T2>::type;  
```  
  
#### 參數  
 `B`  
 判斷這個選取之類型的值。  
  
 `T1`  
 B 為 true 時的類型結果。  
  
 `T2`  
 B 為 false 時的類型結果。  
  
## 備註  
 當 `B` 判斷值為 `true` 時，樣板成員 typedef `conditional<B, T1, T2>::type` 判斷值為 `T1`，當 `B` 判斷值為 `false` 時，判斷值為 `T2`。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)