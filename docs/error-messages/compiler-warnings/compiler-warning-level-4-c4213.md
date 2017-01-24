---
title: "編譯器警告 (層級 4) C4213 | Microsoft Docs"
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
  - "C4213"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4213"
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4213
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：在左值 \(l\-value\) 上進行型別轉換  
  
 使用預設的 Microsoft 擴充功能 \(\/Ze\)，您可以在指派陳述式 \(Assignment Statement\) 的左方使用轉換。  
  
## 範例  
  
```  
// C4213.c  
// compile with: /W4  
void *a;  
void f()  
{  
   int   i[3];  
   a = &i;  
   *(( int * )a )++ = 3;  // C4213  
}  
  
int main()  
{  
}  
```  
  
 這種轉換在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是無效的。