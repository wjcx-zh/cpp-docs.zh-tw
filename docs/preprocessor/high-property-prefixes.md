---
title: "high_property_prefixes | Microsoft Docs"
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
  - "high_property_prefixes"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "high_property_prefixes 屬性"
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# high_property_prefixes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 為三個屬性方法指定替代的前置詞。  
  
## 語法  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### 參數  
 `GetPrefix`  
 由 **propget** 方法所使用的前置字元。  
  
 `PutPrefix`  
 由 **propput** 方法所使用的前置字元。  
  
 `PutRefPrefix`  
 由 **propputref** 方法所使用的前置字元。  
  
## 備註  
 根據預設，高階錯誤處理 **propget**、**propput** 和 **propputref** 方法是由成員函式 \(分別以 **Get**、`Put` 和 **PutRef** 為前置詞命名\) 所公開。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)