---
title: "underlying_type 類別 | Microsoft Docs"
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
  - "underlying_type"
  - "std.underlying_type"
  - "std::underlying_type"
  - "type_traits/std::underlying_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "underlying_type"
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# underlying_type 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生的列舉型別為基礎的整數型別。  
  
## 語法  
  
```  
template <class T>  
    struct underlying_type;  
```  
  
#### 參數  
 `T`  
 要修改的類型。  
  
## 備註  
 `type` 樣板類別的成員 typedef 名稱的基礎整數型別 `T`, ，當 `T` 是列舉型別，否則就沒有成員 typedef `type`。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)