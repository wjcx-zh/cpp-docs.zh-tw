---
title: "decay 類別 | Microsoft Docs"
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
  - "decay"
  - "std.tr1.decay"
  - "std::tr1::decay"
  - "std.decay"
  - "std::decay"
  - "type_traits/std::decay"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "decay 類別 [TR1]"
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# decay 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳值方式傳遞時，會產生型別。 建立類型的非參考、 非常數、 非暫時性或建立類型的指標從函式或陣列型別。  
  
## 語法  
  
```  
template<class T>  
    struct decay;  
  
template<class T> using decay_t = typename decay<T>::type;  
```  
  
#### 參數  
 `T`  
 要修改的類型。  
  
## 備註  
 使用延遲範本產生結果的型別做為引數的值已傳遞的類型。 樣板類別成員 typedef `type` 儲存已修改的類型，這在下列階段定義︰  
  
-   類型 `U` 定義為 `remove_reference<T>::type`。  
  
-   如果 `is_array<U>::value` 為 true，修改過的型別 `type` 是 `remove_extent<U>::type *`。  
  
-   否則，如果 `is_function<U>::value` 為 true，修改過的型別 `type` 是 `add_pointer<U>::type`。  
  
-   否則，修改過的型別 `type` 是 `remove_cv<U>::type`。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)