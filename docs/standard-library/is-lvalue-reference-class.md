---
title: "is_lvalue_reference 類別 | Microsoft Docs"
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
  - "std.tr1.is_lvalue_reference"
  - "std::tr1::is_lvalue_reference"
  - "is_lvalue_reference"
  - "std.is_lvalue_reference"
  - "std::is_lvalue_reference"
  - "type_traits/std::is_lvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_lvalue_reference 類別 [TR1]"
  - "is_lvalue_reference"
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_lvalue_reference 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為 lvalue 參考。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_lvalue_reference;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 類型是物件或函式的參考，則 predicate 類型的執行個體為 true，否則為 false。  請注意，`Ty` 不可以是 rvalue 參考。  如需 rvalue 的詳細資訊，請參閱 [右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)