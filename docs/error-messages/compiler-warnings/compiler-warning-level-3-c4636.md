---
title: "編譯器警告 (層級 3) C4636 | Microsoft Docs"
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
  - "C4636"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4636"
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4636
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

套用至 'construct' 的 XML 文件註解: 標記必須是非空白的 '' 屬性。  
  
 標記 \(如 `cref`\) 沒有值。  
  
## 範例  
 下列範例會產生 C4636。  
  
```  
// C4636.cpp // compile with: /clr /doc /W3 /c /// <see cref=''/> // /// <see cref='System::Exception'/> ref struct A {   // C4636 void f(int); }; // OK /// <see cref='System::Exception'/> ref struct B { void f(int); };  
```