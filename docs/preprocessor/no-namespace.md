---
title: "no_namespace | Microsoft Docs"
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
  - "no_namespace"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_namespace 屬性"
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_namespace
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 指定命名空間名稱不是由編譯器產生。  
  
## 語法  
  
```  
no_namespace  
```  
  
## 備註  
 `#import` 標頭檔中的類型程式庫內容通常是在命名空間中定義。  命名空間名稱是在原始 IDL 檔案的 **library** 陳述式中指定。  如果指定了 `no_namespace` 屬性，則此命名空間名稱不是由編譯器產生。  
  
 如果您要使用不同的命名空間名稱，請使用 [rename\_namespace](../preprocessor/rename-namespace.md) 屬性。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)