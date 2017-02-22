---
title: "編譯器警告 C4485 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4485"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4485"
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 C4485
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override\_function' : 符合基底 ref 類別方法 'base\_class\_function'，但是未標記為 'new' 或 'override'; 假設為 'new' \(且為 'virtual'\)  
  
 存取子會覆寫 \(不管有沒有 `virtual` 關鍵字\) 基底類別存取子函式，但 `override` 或 `new` 規範不是覆寫函式簽章的一部分。  加入 `new` 或 `override` 規範，以解除這項警告。  
  
 如需詳細資訊，請參閱 [override](../../windows/override-cpp-component-extensions.md) 和 [new \(new slot in vtable\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。  
  
 C4485 永遠視同錯誤。  請使用 [warning](../../preprocessor/warning.md) Pragma 隱藏 C4485。  
  
## 範例  
 下列範例會產生 C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```