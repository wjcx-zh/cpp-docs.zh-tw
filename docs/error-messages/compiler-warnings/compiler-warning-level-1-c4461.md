---
title: "編譯器警告 (層級 1) C4461 | Microsoft Docs"
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
  - "C4461"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4461"
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4461
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 這個類別有完成項 'finalizer'，但沒有解構函式 'dtor'  
  
 型別中有完成項暗示資源要刪除。  除非完成項是從型別的解構函式呼叫，Common Language Runtime 會決定您的物件超出範圍以後何時執行完成項。  
  
 如果在型別中定義解構函式，並從解構函式明確呼叫完成項，您可以堅定性地執行完成項。  
  
 如需詳細資訊，請參閱 [解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## 範例  
 下列範例會產生 C4461。  
  
```  
// C4461.cpp  
// compile with: /W1 /clr /c  
ref class A {  
protected:  
   !A() {}   // C4461  
};  
  
// OK  
ref struct B {  
   ~B() {  
      B::!B();  
   }  
  
   !B() {}  
};  
```