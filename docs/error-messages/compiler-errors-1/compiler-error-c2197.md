---
title: "編譯器錯誤 C2197 | Microsoft Docs"
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
  - "C2197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2197"
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 呼叫的引數太多  
  
 編譯器偵測到函式呼叫的參數太多，或函式宣告有誤。  
  
 下列範例會產生 C2197：  
  
```  
// C2197.c // compile with: /Za /c void func( int ); int main() { func( 1, 2 );   // C2197 two actual parameters func( 2 );   // OK }  
```