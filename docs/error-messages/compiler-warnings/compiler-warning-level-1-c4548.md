---
title: "編譯器警告 (層級 1) C4548 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4548"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4548"
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4548
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

逗號之前的運算式無效; 必須是具有副作用的運算式  
  
 編輯器偵測到使用不正確格式的逗號運算式。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4548：  
  
```  
// C4548.cpp  
// compile with: /W1  
#pragma warning (default : 4548)  
int main()  
{  
   int i = 0, k = 0;  
  
   if ( i, k )   // C4548  
   // try the following line instead  
   // if ( i = 0, k )  
      i++;  
}  
```