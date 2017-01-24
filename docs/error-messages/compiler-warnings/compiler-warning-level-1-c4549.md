---
title: "編譯器警告 (層級 1) C4549 | Microsoft Docs"
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
  - "C4549"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4549"
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4549
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 逗號之前的運算子無效; 您要 'operator' 嗎?  
  
 編輯器偵測到使用不正確格式的逗號運算式。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4549：  
  
```  
// C4549.cpp  
// compile with: /W1  
#pragma warning (default : 4549)  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( i == 0, k )   // C4549  
   // try the following line instead  
   // if ( i == 0 )  
      i++;  
}  
```