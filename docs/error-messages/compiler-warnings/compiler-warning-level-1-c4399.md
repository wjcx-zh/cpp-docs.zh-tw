---
title: "編譯器警告 (層級 1) C4399 | Microsoft Docs"
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
  - "C4399"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4399"
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4399
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 用 \/clr:pure 編譯時，處理序專屬符號不應以 \_\_declspec\(dllimport\) 標記  
  
 來自原生映像的資料或有原生和 CLR 建構的映像不能匯入純映像之中。  若要解除這項警告，請以 **\/clr** \(不是 **\/clr:pure**\) 編譯，或刪除 `__declspec(dllimport)`。  
  
## 範例  
 下列範例會產生 C4399：  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```