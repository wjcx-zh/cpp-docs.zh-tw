---
title: "編譯器錯誤 C2930 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2930"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2930"
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2930
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': type\-class\-id 重新定義為 'enum identifier' 的列舉值  
  
 您無法使用泛型或樣板類別作為列舉的成員。  
  
 此錯誤可能是大括弧不對稱所造成。  
  
 下列範例會產生 C2930：  
  
```  
// C2930.cpp // compile with: /c template<class T> class x{}; enum SomeEnum { x };   // C2930 class y{}; enum SomeEnum { y };  
```  
  
 使用泛型時，也會發生 C2930：  
  
```  
// C2930c.cpp // compile with: /clr /c generic<class T> ref struct GC {}; enum SomeEnum { GC };   // C2930 ref struct GC2 {}; enum SomeEnum2 { GC2 };  
```