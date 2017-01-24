---
title: "raw_interfaces_only | Microsoft Docs"
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
  - "raw_interfaces_only"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_interfaces_only 屬性"
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_interfaces_only
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 不產生錯誤處理包裝函式以及使用這些包裝函式的 [property](../cpp/property-cpp.md) 宣告。  
  
## 語法  
  
```  
raw_interfaces_only  
```  
  
## 備註  
 `raw_interfaces_only` 屬性 \(Attribute\) 也會造成用於命名非屬性 \(Property\) 函式的預設前置詞遭到移除。  通常前置詞為 **raw\_**。  如果指定這個屬性，函式名稱會直接來自類型程式庫。  
  
 這個屬性只能讓您公開類型程式庫中的低階內容。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)