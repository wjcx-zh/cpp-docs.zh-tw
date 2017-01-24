---
title: "編譯器警告 (層級 4) C4205 | Microsoft Docs"
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
  - "C4205"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4205"
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4205
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：在函式範圍中的靜態函式宣告  
  
 使用 Microsoft 擴充功能 \(\/Ze\)，您可以在其他函式中宣告**靜態**函式。  此函式為全域範圍的函式。  
  
## 範例  
  
```  
// C4205.c  
// compile with: /W4  
void func1()  
{  
   static int func2();  // C4205  
};  
  
int main()  
{  
}  
```  
  
 這樣的初始化設定在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是無效的。