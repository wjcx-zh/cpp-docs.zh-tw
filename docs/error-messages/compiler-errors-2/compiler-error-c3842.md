---
title: "編譯器錯誤 C3842 | Microsoft Docs"
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
  - "C3842"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3842"
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3842
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function'：不支援 WinRT 或 Managed 類型的成員函式上的 'const' 和 'volatile' 限定詞  
  
 不支援 Windows 執行階段或 Managed 類型的成員函式上的 [const](../../cpp/const-cpp.md) 和 [volatile](../../cpp/volatile-cpp.md)。  
  
 下列範例會產生 C3842：  
  
```  
// C3842a.cpp  
// compile with: /clr /c  
public ref struct A {  
   void f() const {}   // C3842  
   void f() volatile {}   // C3842  
  
   void f() {}  
};  
  
```