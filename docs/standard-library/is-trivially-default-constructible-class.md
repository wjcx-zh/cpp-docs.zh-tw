---
title: "is_trivially_default_constructible 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_default_constructible"
  - "std.is_trivially_default_constructible"
  - "std::is_trivially_default_constructible"
  - "type_traits/std::is_trivially_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_default_constructible"
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# is_trivially_default_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有 trivial 預設建構函式。  
  
## 語法  
  
```  
template<class Ty>  
    struct  is_trivially_default_constructible;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 類型是具有 trivial 建構函式的類別，則類型述詞的執行個體保留 true，否則保留 false。  
  
 在下列情況下，類別 `Ty` 的預設建構函式是 trivial：  
  
-   它是以隱含方式宣告的預設建構函式  
  
-   類別 `Ty` 沒有虛擬函式  
  
-   類別 `Ty` 沒有虛擬基底  
  
-   類別 `Ty` 的所有直接基底都有 trivial 建構函式  
  
-   類別類型的所有非靜態資料成員的類別都具有 trivial 建構函式  
  
-   類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 建構函式  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)