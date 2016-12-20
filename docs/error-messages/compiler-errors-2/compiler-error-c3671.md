---
title: "編譯器錯誤 C3671 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3671"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3671"
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3671
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function\_1' : 函式未覆寫 'function\_2'  
  
 使用明確的覆寫語法時，如果未覆寫函式，編譯器會產生錯誤。如需詳細資訊，請參閱[Explicit Overrides](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3671。  
  
```  
// C3671.cpp  
// compile with: /clr /c  
ref struct S {  
   virtual void f();  
};  
  
ref struct S1 : S {  
   virtual void f(int) new sealed = S::f;   // C3671  
   virtual void f() new sealed = S::f;  
};  
```