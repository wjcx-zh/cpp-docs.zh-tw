---
title: "hash 結構 | Microsoft Docs"
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
  - "typeindex/std::hash"
dev_langs: 
  - "C++"
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別將它的方法定義為傳回 `val.hash_code()`。 方法會定義雜湊函式，用來將類型 [type\_index](../standard-library/type-index-class.md) 的值對應至索引值分佈。  
  
## 語法  
  
```vb  
template<>  
    struct hash<type_index>  
        : public unary_function<type_index, size_t>  
    { // hashes a typeinfo object  
    size_t operator()(type_index val) const;  
    };  
```  
  
## 請參閱  
 [\<typeindex\>](../standard-library/typeindex.md)