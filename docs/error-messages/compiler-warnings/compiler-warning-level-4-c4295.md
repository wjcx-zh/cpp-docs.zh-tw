---
title: "編譯器警告 (層級 4) C4295 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4295"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4295"
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 編譯器警告 (層級 4) C4295
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**'**   
 ***array* '：陣列太小無法包含結束的 null 字元**  
  
 一個陣列經過初始化，但是陣列的最後一個字元不是 Null 字元；存取該陣列可能會造成非預期的結果。  
  
 下列範例會產生 C4295：  
  
```  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```