---
title: "編譯器警告 C4972 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4972"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4972"
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4972
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

直接修改或將 Unbox 作業的結果視為左值，將無法驗證  
  
 對實值類型的控制代碼取值 \(也稱為 Unboxing\)，然後指派給它，這個作業無法驗證。  
  
 如需詳細資訊，請參閱[Boxing](../../windows/boxing-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4972。  
  
```  
// C4972.cpp // compile with: /clr:safe using namespace System; ref struct R { int ^ p;   // a value type }; int main() { R ^ r = gcnew R; *(r->p) = 10;   // C4972 // OK r->p = 10; Console::WriteLine( r->p ); Console::WriteLine( *(r->p) ); }  
```