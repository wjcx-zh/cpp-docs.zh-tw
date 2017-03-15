---
title: "編譯器警告 (層級 1) C4486 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4486"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4486"
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 編譯器警告 (層級 1) C4486
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : ref 類別或實值類別的私用虛擬方法應該標記為 'sealed'  
  
 因為 Managed 類別或結構的私用虛擬成員函式無法存取或覆寫，它應該標記為 [sealed](../../windows/sealed-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4486。  
  
```  
// C4486.cpp  
// compile with: /clr /c /W1  
ref class B {  
private:  
   virtual void f() {}   // C4486  
   virtual void f1() sealed {}   // OK  
};  
```  
  
## 範例  
 下列範例將示範私用密封虛擬函式的一種可能用法。  
  
```  
// C4486_b.cpp  
// compile with: /clr /c  
ref class B {};  
  
ref class D : B {};  
  
interface class I {  
   B^ mf();  
};  
  
ref class E : I {  
private:  
   virtual B^ g() sealed = I::mf {  
      return gcnew B;  
   }  
  
public:  
   virtual D^ mf() {  
      return gcnew D;  
   }  
};  
```