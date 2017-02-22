---
title: "編譯器警告 (層級 3) C4645 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4645"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4645"
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 3) C4645
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 \_\_declspec\(noreturn\) 宣告的函式有傳回的陳述式  
  
 在函式中找到以 [noreturn](../../cpp/noreturn.md)`__declspec` 修飾詞標記的 [return](../../cpp/return-statement-in-program-termination-cpp.md) 陳述式。 已忽略 `return` 陳述式。  
  
 下列範例會產生 C4645：  
  
```  
// C4645.cpp // compile with:  /W3 void __declspec(noreturn) func() { return;   // C4645, delete this line to resolve } int main() { }  
```