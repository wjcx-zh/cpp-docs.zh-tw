---
title: "high_method_prefix | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "high_method_prefix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "high_method_prefix 屬性"
ms.assetid: cacebf09-12f5-4919-ad40-939e206e340c
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# high_method_prefix
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 指定用來命名高階屬性和方法的前置詞。  
  
## 語法  
  
```  
high_method_prefix("Prefix")  
```  
  
#### 參數  
 `Prefix`  
 要使用的前置詞。  
  
## 備註  
 根據預設，高階錯誤處理屬性和方法會由名稱不含前置詞的成員函式公開。  其名稱來自於類型程式庫。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)