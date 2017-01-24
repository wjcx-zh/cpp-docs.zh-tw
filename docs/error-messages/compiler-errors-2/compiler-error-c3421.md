---
title: "編譯器錯誤 C3421 | Microsoft Docs"
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
  - "C3421"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3421"
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3421
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 您不能呼叫這個類別的完成項，因為它無法存取，或者不存在  
  
 完成項是隱含私用的，因此無法從其封入類型外部呼叫。  
  
 如需詳細資訊，請參閱[Visual C\+\+ 中的解構函式和完成項](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C3421。  
  
```  
// C3421.cpp // compile with: /clr ref class A {}; ref class B { !B() {} public: ~B() {} }; int main() { A a; a.!A();   // C3421 B b; b.!B();   // C3421 }  
```