---
title: "make_unsigned 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.make_unsigned"
  - "make_unsigned"
  - "std::tr1::make_unsigned"
  - "std.make_unsigned"
  - "std::make_unsigned"
  - "type_traits/std::make_unsigned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_unsigned 類別 [TR1]"
  - "make_unsigned"
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# make_unsigned 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立類型，或是建立大於或等於類型大小的最小無正負號類型。  
  
## 語法  
  
```  
template<class T>  
    struct make_unsigned;  
  
template<class T>  
    using make_unsigned_t = typename make_unsigned<T>::type;  
  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`T`|要修改的類型。|  
  
## 備註  
 如果 `is_unsigned<T>` 為 true，則 modifier 類型的執行個體所保留的修改類型是 `T`。  否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)