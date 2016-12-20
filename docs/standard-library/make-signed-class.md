---
title: "make_signed 類別 | Microsoft Docs"
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
  - "std::tr1::make_signed"
  - "make_signed"
  - "std.tr1.make_signed"
  - "std.make_signed"
  - "std::make_signed"
  - "type_traits/std::make_signed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_signed 類別 [TR1]"
  - "make_signed"
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# make_signed 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立類型，或是建立大於或等於類型大小的最小帶正負號類型。  
  
## 語法  
  
```  
template<class T>  
    struct make_signed;  
  
template<class T>  
    using make_signed_t = typename make_signed<T>::type;  
```  
  
#### 參數  
 `T`  
 要修改的類型。  
  
## 備註  
 如果 `is_signed<T>` 為 true，則 modifier 類型的執行個體所保留的修改類型是 `T`。 否則，是最小的未帶正負號類型 `UT`，其中 `sizeof (T) <= sizeof (UT)`。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)