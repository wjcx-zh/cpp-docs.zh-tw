---
title: "編譯器錯誤 C2814 | Microsoft Docs"
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
  - "C2814"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2814"
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2814
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member'：原生類型不可以巢狀方式置於 Managed 或 WinRT 類型 'type' 中  
  
## 範例  
 原生類型不可以巢狀方式置於 CLR 或 WinRT 類型中。  下列範例會產生 C2814，並示範如何修正此問題。  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
  
## 範例  
 使用 Managed Extensions for C\+\+，您必須使用下列其中一個關鍵字，明確指定內嵌類型的「管理性質」：[\_\_gc](../../misc/gc.md)、[\_\_nogc](../../misc/nogc.md) 或 [\_\_value](../../misc/value.md)。  
  
 下列範例會產生 C2814，並示範如何修正此問題。  
  
```  
// C2814_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class A {  
   class B {};   // C2814  
   __gc class C {};   // OK  
};  
```