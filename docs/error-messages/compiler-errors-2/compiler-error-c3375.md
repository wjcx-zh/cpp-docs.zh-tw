---
title: "編譯器錯誤 C3375 | Microsoft Docs"
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
  - "C3375"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3375"
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3375
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 模稜兩可的委派函式  
  
 委派具現化可能已指派給靜態成員函式，或作為執行個體函式的未繫結委派，因此編譯器會發出這個錯誤。  
  
 如需詳細資訊，請參閱[delegate](../../windows/delegate-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3375。  
  
```  
// C3375.cpp // compile with: /clr ref struct R { static void f(R^) {} void f() {} }; delegate void Del(R^); int main() { Del ^ a = gcnew Del(&R::f);   // C3375 }  
```