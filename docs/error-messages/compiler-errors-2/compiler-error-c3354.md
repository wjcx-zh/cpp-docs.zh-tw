---
title: "編譯器錯誤 C3354 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3354"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3354"
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C3354
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 用來建立委派的函式不可以擁有傳回類型 'type'  
  
 下列類型作為[委派](../../misc/delegate.md)的傳回類型時無效：  
  
-   函式的指標  
  
-   成員的指標  
  
-   成員函式的指標  
  
-   函式的參考  
  
-   成員函式的參考  
  
 下列範例會產生 C3354：  
  
```  
// C3354_2.cpp // compile with: /clr /c using namespace System; typedef void ( *VoidPfn )(); delegate VoidPfn func(); // C3354 // try the following line instead // delegate  void func();  
```  
  
 下列範例會產生 C3354：  
  
```  
// C3354.cpp // compile with: /clr:oldSyntax /c #using <mscorlib.dll> using namespace System; typedef void (*VoidPfn)(); __delegate VoidPfn func();   // C3354 // try the following line instead // __delegate void func();  
```