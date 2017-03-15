---
title: "編譯器警告 (層級 1) C4230 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4230"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4230"
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4230
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

過時的用法：修飾詞\/限定詞位置顛倒；已忽略限定詞  
  
 在 `__cdecl` 之類的 Microsoft 修飾詞之前使用限定詞是過時的做法。  
  
## 範例  
  
```  
// C4230.cpp  
// compile with: /W1 /LD  
int __cdecl const function1();   // C4230 const ignored  
```