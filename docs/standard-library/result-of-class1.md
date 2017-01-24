---
title: "result_of 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "result_of"
  - "std.result_of"
  - "std::result_of"
  - "type_traits/std::result_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "result_of"
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# result_of 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

決定傳回的型別之型別的可呼叫使用指定的引數類型。  
  
## 語法  
  
```  
template <class Fn, class... ArgTypes>  
    struct result_of<Fn(ArgTypes...)>;  
```  
  
#### 參數  
 `Fn`  
 要查詢的可呼叫類型。  
  
 `ArgTypes`  
 要查詢的可呼叫類型的引數清單型別。  
  
## 備註  
 此範本可用來判斷在編譯時期的結果型別 `Fn`\(`ArgTypes`\)，其中 `Fn` 是使用中的型別引數清單叫用可呼叫的型別 `ArgTypes`。`type` 樣板類別成員名稱的結果型別 `decltype(INVOKE(declval<Fn>(), declval<ArgTypes>()...))` 如果未評估的運算式 `INVOKE(declval<Fn>(), declval<ArgTypes>()...)` 是格式正確。 否則，此樣板類別具有沒有成員 `type`。 型別 `Fn` 和參數組件中的所有型別 `ArgTypes` 必須是完整的型別， `void`, ，或無法辨識的繫結的陣列。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)