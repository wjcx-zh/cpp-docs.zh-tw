---
title: "編譯器錯誤 C3283 | Microsoft Docs"
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
  - "C3283"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3283"
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3283
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 介面不能有執行個體建構函式  
  
 CLR [介面](../../windows/interface-class-cpp-component-extensions.md)不能有執行個體建構函式。  允許靜態建構函式。  
  
 下列範例會產生 C3283：  
  
```  
// C3283.cpp // compile with: /clr interface class I { I();   // C3283 };  
```  
  
 可能的解決方式：  
  
```  
// C3283b.cpp // compile with: /clr /c interface class I { static I(){} };  
```