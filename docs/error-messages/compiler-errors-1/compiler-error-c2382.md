---
title: "編譯器錯誤 C2382 | Microsoft Docs"
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
  - "C2382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2382"
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function'：重複定義; 不同的例外狀況規格  
  
 在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，此錯誤表示嘗試只在[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)執行函式多載。  
  
 下列範例會產生 C2382：  
  
```  
// C2382.cpp // compile with: /Za /c void f1(void) throw(int) {} void f1(void) throw(char) {}   // C2382 void f2(void) throw(char) {}   // OK  
```