---
title: "no_auto_exclude | Microsoft Docs"
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
  - "no_auto_exclude"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_auto_exclude 屬性"
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_auto_exclude
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 停用自動排除。  
  
## 語法  
  
```  
no_auto_exclude  
```  
  
## 備註  
 類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。  `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。  這樣做將會針對每個要排除的項目發出 [編譯器警告 \(層級 3\) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)。  您可以使用這個屬性停用這種自動排除行為。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)