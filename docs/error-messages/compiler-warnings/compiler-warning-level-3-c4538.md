---
title: "編譯器警告 (層級 3) C4538 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4538"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4538"
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器警告 (層級 3) C4538
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 不支援這種型別上的 const\/volatile 限定詞  
  
 限定詞 \(Qualifier\) 關鍵字不正確地套用至陣列。  如需詳細資訊，請參閱[陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C4538：  
  
```  
// C4538.cpp  
// compile with: /clr /W3 /LD  
const array<int> ^f1();   // C4538  
array<const int> ^f2();   // OK  
```