---
title: "編譯器警告 (層級 4) C4815 | Microsoft Docs"
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
  - "C4815"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4815"
ms.assetid: 99081928-d7d5-4dce-b4af-7c6a151bfac0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4815
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 堆疊物件中大小為零的陣列將沒有元素 \(除非該物件是經過彙總初始化的彙總\)  
  
 具有未定義的元素數量的陣列 \(大小為零的陣列\)，是型別的最後一位成員，而且已在堆疊上建立該型別的物件。  將不會為陣列配置任何記憶體。  如果您需要有用的建構函式 \(Constructor\)，您可以在堆積上為 struct 配置記憶體。  
  
 下列範例會產生 C4815：  
  
```  
// C4815.cpp  
// compile with: /W4  
#include <memory>  
#pragma warning(disable : 4200)  
struct S1  
{  
   int i;  
   char cArr[];  
};  
  
S1 s1_glb;   // C4815 stack object with zero-array (not aggregate inited)  
// try the following line instead  
// S1 s1_glb = { 0, 0, 0 };  
  
struct S2  
{  
   S2(int _i) : i(_i) {}  
   int i;  
   char cArr[];  
};  
  
S2 s2_glb1(10);   // C4815  
// try the following line instead  
// S2 s2_glb1 = { 10 };  // to work, comment the constructor  
  
int main()  
{  
   S1 s1_loc1;   // C4815  
   // try the following line instead  
   // S1 s1_loc1 = { 0 };  
  
   S1 s1_loc2 = { 1, { 'a', 'b', 'c' } };  
  
   S1 s1_loc3 = s1_loc2;   // C4815 truncation when copy ctor called  
   // truncation if call a compiler-generated copy constructor  
   // to copy a struct with a zero sized array in it  
   s1_loc1;  
   s1_loc2;  
   s1_loc3;  
  
   // allocate memory for struct on heap  
   int nEle = 10;   // allocate 10 chars for char array  
   void * pV = malloc (sizeof(S2) + nEle * sizeof(char));  
   S2 *pS1 = new (pV) S2(nEle);  
   pS1;  
}  
```