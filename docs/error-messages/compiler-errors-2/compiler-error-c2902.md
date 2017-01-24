---
title: "編譯器錯誤 C2902 | Microsoft Docs"
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
  - "C2902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2902"
ms.assetid: 89d78d0e-78e5-4c2c-a0f9-a60110e9395e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2902
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'token': 'template' 之後有未預期的語彙基元，必須是識別項  
  
 關鍵字 `template` 後面的語彙基元不是識別項。  
  
 下列範例會產生 C2902：  
  
```  
// C2902.cpp // compile with: /c namespace N { template<class T> class X {}; class Y {}; } void g() { N::template + 1;   // C2902 } void f() { N::template X<int> x1;   // OK }  
```  
  
 使用泛型時，也會發生 C2902：  
  
```  
// C2902b.cpp // compile with: /clr /c namespace N { generic<class T> ref class GC {}; } void f() { N::generic + 1;   // C2902 N::generic GC<int>^ x; }  
```