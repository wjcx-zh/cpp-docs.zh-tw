---
title: "編譯器錯誤 C3648 | Microsoft Docs"
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
  - "C3648"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3648"
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3648
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個明確覆寫語法必須有 \/clr:oldSyntax  
  
 為最新 Managed 語法進行編譯時，編譯器發現舊版的明確覆寫語法。  
  
 如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。  如需舊版語法的詳細資訊，請參閱[明確覆寫](../../cpp/explicit-overrides-cpp.md)。  
  
 下列範例會產生 C3648：  
  
```  
// C3648.cpp  
// compile with: /clr  
public interface struct I {  
   void f();  
};  
  
public ref struct R : I {  
   virtual void I::f() {}   // C3648  
   // try the following line instead  
   // virtual void f() = I::f{}  
};  
```