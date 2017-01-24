---
title: "編譯器警告 (層級 1) C4155 | Microsoft Docs"
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
  - "C4155"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4155"
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4155
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除陣列運算式沒有使用陣列形式的 'delete'  
  
 陣列形式的 **delete** 應該用於刪除陣列。 這個警告只會在遵守 ANSI 相容性 \(\/Za\) 時發生。  
  
## 範例  
 下列範例會產生 C4155：  
  
```  
// C4155.cpp // compile with: /Za /W1 #include <stdio.h> int main(void) { int (*array)[ 10 ] = new int[ 5 ] [ 10 ]; array[0][0] = 8; printf_s("%d\n", array[0][0]); delete array;   // C4155 // try the following line instead // delete [] array;   // C4155 }  
```