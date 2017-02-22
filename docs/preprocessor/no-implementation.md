---
title: "no_implementation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_implementation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_implementation 屬性"
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# no_implementation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 不產生 .tli 標頭，其中包含包裝函式成員函式的實作。  
  
## 語法  
  
```  
no_implementation  
```  
  
## 備註  
 如果已指定這個屬性，則會產生 .tlh 標頭 \(具有公開類型程式庫項目的宣告\)，但沒有 `#include` 陳述式可包含 .tli 標頭檔。  
  
 這個屬性會搭配 [implementation\_only](../preprocessor/implementation-only.md) 使用。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)