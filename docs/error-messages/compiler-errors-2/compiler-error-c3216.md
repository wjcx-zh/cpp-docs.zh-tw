---
title: "編譯器錯誤 C3216 | Microsoft Docs"
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
  - "C3216"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3216"
ms.assetid: bbab1efe-8779-4489-8bb0-b11e45f5cbe5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3216
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

條件約束必須是泛型參數，而非 'type'  
  
 條件約束的格式錯誤。  
  
 下列範例會產生 C3216：  
  
```  
// C3216.cpp // compile with: /clr interface struct A {}; generic <class T> where F : A   // C3216 // Try the following line instead: // where T : A    // C3216 ref class C {};  
```  
  
 下列範例示範可能的解決方式：  
  
```  
// C3216b.cpp // compile with: /clr /c interface struct A {}; generic <class T> where T : A ref class C {};  
```