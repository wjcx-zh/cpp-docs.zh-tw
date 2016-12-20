---
title: "編譯器錯誤 C3609 | Microsoft Docs"
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
  - "C3609"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3609"
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3609
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member'：密封或最終函式必須為虛擬  
  
 [密封](../../windows/sealed-cpp-component-extensions.md)和[最終](../../cpp/final-specifier.md)關鍵字僅能使用於標示 `virtual` 的類別、結構或成員函式。  
  
 下列範例會產生 C3609：  
  
```  
// C3609.cpp  
// compile with: /clr /c  
ref class C {  
   int f() sealed;   // C3609  
   virtual int f2() sealed;   // OK  
};  
```  
  
 **Managed Extensions for C\+\+**  
  
 下列範例會產生 C3609：  
  
```  
// C3609c.cpp  
// compile with: /clr:oldSyntax /c  
__gc class C {  
   __sealed int f();   // C3609  
   __sealed virtual int f2();   // OK  
};  
```