---
title: "raw_method_prefix | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "raw_method_prefix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_method_prefix 屬性"
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# raw_method_prefix
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 指定不同的前置詞，避免發生名稱衝突。  
  
## 語法  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### 參數  
 `Prefix`  
 要使用的前置詞。  
  
## 備註  
 低層級的屬性和方法是由名稱含前置詞 **raw\_** 的成員函式公開，以避免與高階錯誤處理成員函式的名稱衝突。  
  
> [!NOTE]
>  `raw_method_prefix` 屬性的作用不會因為 [raw\_interfaces\_only](#_predir_raw_interfaces_only) 屬性的存在而變更。  在指定前置詞時，`raw_method_prefix` 一定會優先於 `raw_interfaces_only`。  如果在相同的 `#import` 陳述式中使用了這兩個屬性，則會使用 `raw_method_prefix` 屬性指定的前置詞。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)