---
title: "編譯器錯誤 C2490 | Microsoft Docs"
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
  - "C2490"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2490"
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2490
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允許在具有 'naked' 屬性的函式中使用 'keyword'  
  
 定義成 [naked](../../cpp/naked-cpp.md) 的函式不能使用結構化例外狀況處理 \(Structured Exception Handling\)。  
  
 下列範例會產生 C2490：  
  
```  
// C2490.cpp  
// processor: x86  
__declspec( naked ) int func() {  
   __try{}   // C2490, structured exception handling  
}  
```