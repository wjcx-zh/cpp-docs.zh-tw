---
title: "編譯器警告 (層級 1) C4218 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4218"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4218"
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4218
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：必須指定至少一個儲存類別或型別  
  
 使用預設的 Microsoft 擴充功能 \(\/Ze\)，您可以宣告變數但不需指定型別或儲存類別。  預設型別為 `int`。  
  
## 範例  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 這樣的宣告在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是無效的。