---
title: "include() | Microsoft Docs"
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
  - "include()"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "include() 屬性"
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# include()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 停用自動排除。  
  
## 語法  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### 參數  
 `Name1`  
 要強制包含的第一個項目。  
  
 `Name2`  
 要強制包含的第二個項目 \(如果需要的話\)。  
  
## 備註  
 類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。  `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。  如果項目已排除 \(如 [編譯器警告 \(層級 3\) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) 所指\)，但是不應該排除這些項目，則可以使用這個屬性來停用自動排除。  這個屬性可以接受任意數目的引數，每個引數都會是要包含的類型程式庫項目名稱。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)