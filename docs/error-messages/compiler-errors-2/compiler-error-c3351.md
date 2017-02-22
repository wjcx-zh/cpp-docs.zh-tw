---
title: "編譯器錯誤 C3351 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3351"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3351"
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C3351
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'object': 委派建構函式：第二個引數必須是靜態成員函式或全域函式的位址  
  
 編譯器必須有宣告為 [static](../../misc/static-cpp.md) 之函式的位址。  
  
 下列範例會產生 C3351：  
  
```  
// C3351a.cpp // compile with: /clr delegate int D(int, int); ref class C { public: int mf(int, int) { return 1; } static int mf2(int, int) { return 1; } }; int main() { System::Delegate ^pD = gcnew D(nullptr, &C::mf);   // C3351 System::Delegate ^pD2 = gcnew D(&C::mf2); }  
```  
  
 下列範例會產生 C3351：  
  
```  
// C3351b.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> __delegate int D(int, int); __gc class C { public: int mf(int, int) { // declare the function as static // static int mf(int, int) { return 1; } }; int main() { C *pC = new C; System::Delegate *pD = new D(0, &C::mf);   // C3351 }  
```