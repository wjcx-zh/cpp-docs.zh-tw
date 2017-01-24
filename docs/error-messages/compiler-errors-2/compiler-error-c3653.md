---
title: "編譯器錯誤 C3653 | Microsoft Docs"
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
  - "C3653"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3653"
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3653
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 不可當做具名覆寫使用: 找不到要被覆寫的函式，您是否忘了用 :: 運算子明確指明這個函式?  
  
 明確的覆寫指定了在任何介面中都找不到的函式。  如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下列範例會產生 C3653：  
  
```  
// C3653.cpp  
// compile with: /clr  
public interface struct I {  
   void h();  
};  
  
public ref struct X : public I {  
   virtual void f() new sealed = J {};   // C3653 no J in scope  
   virtual void g() {}   // OK  
   virtual void h() new sealed = I::h {};   // OK  
};  
```