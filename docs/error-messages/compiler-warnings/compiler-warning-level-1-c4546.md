---
title: "編譯器警告 (層級 1) C4546 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4546"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4546"
ms.assetid: 071e1709-3841-46c1-8e71-96109cd22041
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4546
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

逗號之前的函式呼叫遺漏引數清單  
  
 編輯器偵測到使用不正確格式的逗號運算式。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 範例  
 下列範例會產生 C4546：  
  
```  
// C4546.cpp  
// compile with: /W1  
#pragma warning (default : 4546)  
void f(int i) {  
   i++;  
}  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( f, k )   // C4546  
   // try the following line instead  
   // if ( f(i), k )  
      i++;  
}  
```