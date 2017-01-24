---
title: "exclude (#import) | Microsoft Docs"
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
  - "exclude"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "exclude 屬性"
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exclude (#import)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 排除從類型程式庫標頭檔產生的項目。  
  
## 語法  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### 參數  
 `Name1`  
 要排除的第一個項目。  
  
 `Name2`  
 要排除的第二個項目 \(如果需要的話\)。  
  
## 備註  
 類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。  這個屬性可以接受任意數目的引數，每一個都是要排除的頂層類型程式庫項目。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)