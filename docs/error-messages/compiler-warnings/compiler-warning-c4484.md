---
title: "編譯器警告 C4484 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4484"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4484"
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 C4484
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override\_function' : 符合基底 ref 類別方法 'base\_class\_function'，但是未標記為 'virtual'、'new' 或 'override'; 假設為 'new' \(而非 'virtual'\)  
  
 使用 **\/clr** 編譯時，編譯器不會以隱含方式覆寫基底類別函式，也就是說，函式將在 vtable 中取得新位置。  若要解決這個問題，請明確指定函式是否為多載。  
  
 如需詳細資訊，請參閱：  
  
-   [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [new \(new slot in vtable\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 C4484 永遠視同錯誤。  請使用 [warning](../../preprocessor/warning.md) Pragma 隱藏 C4484。  
  
## 範例  
 下列範例會產生 C4484。  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```