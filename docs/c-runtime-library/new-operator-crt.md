---
title: "運算子 new(CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "new[]"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator new[]"
  - "vector new"
ms.assetid: 79682f85-6889-40f6-b8f7-9eed5176ea35
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算子 new(CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從堆積配置記憶體區塊。  
  
## 語法  
  
```  
  
      void *__cdecl operator new[](size_t count);  
void *__cdecl operator new[] (  
   size_t count,   
   void * object  
) throw();  
void *__cdecl operator new[] (  
   size_t count,   
   const std::nothrow_t&  
) throw();  
```  
  
#### 參數  
 *count*  
 配置的區段大小。  
  
 *object*  
 指向建立物件記憶體區塊的指標。  
  
## 傳回值  
 新配置儲存區之最低位元組位址的指標。  
  
## 備註  
 `operator new`的是新的向量表單，與新的純量表單\([新運算子](../c-runtime-library/operator-new-crt.md)\)。  
  
 第一種形式的運算子稱為無放置 \(nonplacement\) 形式。  這個運算子的第二分表單稱為placement 表單，而這個運算子第三種形式是 nonthrowing，placement表單。  
  
 運算子的第一個形式是由編譯器定義的，而且不需要 new.h 包括在您的程式中。  
  
 [operator delete&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) 新運算子配置的可用記憶體。  
  
 您可以設定`operator new[]`的傳回值為 NULL 或在失敗時擲回的例外狀況。  如需詳細資訊，請參閱新的 [新增與移除運算子](../cpp/new-and-delete-operators.md) 。  
  
 加上了擲回的或無擲回例外的行為後， CRT  `operator new` 則與在 Standard C\+\+ 程式庫中的[operator new&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md)行為相同。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`new[]`|\<new.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 下列範例顯示如何使用向量， `operator new`的 nonplacement 表單。  
  
```  
// crt_new4.cpp  
#include <stdio.h>  
int main() {  
   int * k = new int[10];  
   k[0] = 21;  
   printf("%d\n", k[0]);  
   delete [] k;  
}  
```  
  
 下列範例顯示如何使用向量， `operator new`的放置表單。  
  
```  
// crt_new5.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * i = new int[10];  
   i[0] = 21;  
   printf("%d\n", i[0]);  
   // initialize existing memory (i) with, in this case, int[[10]  
   int * j = new(i) int[10];   // placement vector new  
   printf("%d\n", j[0]);  
   j[0] = 22;  
   printf("%d\n", i[0]);  
   delete [] i;   // or, could have deleted [] j   
}  
```  
  
 下列範例顯示如何使用向量， `operator new`的放置，不擲回表單。  
  
```  
// crt_new6.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * k = new(std::nothrow) int[10];  
   k[0] = 21;  
   printf("%d\n", k[0]);  
   delete [] k;  
}  
```  
  
## 請參閱  
 [記憶體配置](../c-runtime-library/memory-allocation.md)