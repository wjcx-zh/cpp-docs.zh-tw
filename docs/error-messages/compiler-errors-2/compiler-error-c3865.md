---
title: "編譯器錯誤 C3865 | Microsoft Docs"
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
  - "C3865"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3865"
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3865
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'calling\_convention' : 只能使用於原生成員函式  
  
 將呼叫慣例用在全域函式或 Managed 成員函式上。  該呼叫慣例只能用在原生 \(Managed\) 成員函式上。  
  
 如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。  
  
 下列範例會產生 C3865：  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```