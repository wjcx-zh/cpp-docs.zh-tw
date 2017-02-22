---
title: "編譯器錯誤 C2084 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2084"
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式 'function' 的主體已經被宣告了  
  
 函式已經完成定義。  
  
 在舊版的 Visual C\+\+ 中，  
  
-   在沒有其他的定義可用的情況下，編譯器仍會接受多個解析成同一實際型別的樣板特製化。  現在編譯器將偵測這些定義。  
  
-   \_\_int32 和 int 以前被視為不同型別。  現在，編譯器將 \_\_int32 視為 int 的同義字。  這表示如果在 \_\_int32 和 int 上發生多載某個函式並產生錯誤，則編譯器將會偵測多項定義。  
  
 下列範例會產生 C2084：  
  
```  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
 可能的解決方案：  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```