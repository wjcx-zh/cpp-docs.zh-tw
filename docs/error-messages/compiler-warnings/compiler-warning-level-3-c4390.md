---
title: "編譯器警告 (層級 3) C4390 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4390"
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 3) C4390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

';' : 找到空白的控制陳述式; 這是想要的?  
  
 在不包含指令的控制陳述式之後找到分號。  
  
 如果您因為巨集而取得 C4390，您應該用 [warning](../../preprocessor/warning.md) Pragma 在包含該巨集的模組中關閉 C4390。  
  
 下列範例會產生 C4390：  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```