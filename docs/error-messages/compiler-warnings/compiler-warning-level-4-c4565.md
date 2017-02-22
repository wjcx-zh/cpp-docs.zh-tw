---
title: "編譯器警告 (層級 4) C4565 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4565"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4565"
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 4) C4565
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 重複定義，這個符號先前是以 \_\_declspec\(modifier\) 宣告的  
  
 符號是重複定義或重新宣告，而第二個定義或宣告跟第一個定義或宣告不同，並沒有 `__declspec` 修飾詞 \(***modifier***\)。  這項警告僅供參考，  若要解除這項警告，請刪除其中一個定義。  
  
 下列範例會產生 C4565：  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```