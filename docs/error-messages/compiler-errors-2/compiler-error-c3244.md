---
title: "編譯器錯誤 C3244 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3244"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3244"
ms.assetid: dae6c49b-5212-4206-8f61-d4010c0b9969
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3244
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method': 此方法是由 'interface' 引入，而非由 'interface'  
  
 您已嘗試[明確覆寫](../../cpp/explicit-overrides-cpp.md)不存在於所指定介面但存在於另一個基底類別中的成員。  
  
 下列範例會產生 C3244：  
  
```  
// C3244.cpp #pragma warning(disable:4199) __interface IX15A { void f(); }; __interface IX15B { void g(); }; class CX15 : public IX15A, public IX15B { public: void IX15A::f(); void IX15B::g(); }; void CX15::IX15A::g()   // C3244 occurs here { }  
```