---
title: "operator new (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator new"
  - "scalar new"
ms.assetid: 4ae51618-a4e6-4172-b324-b99d86d1bdca
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator new (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從堆積配置記憶體區塊。  
  
## 語法  
  
```  
  
      void *__cdecl operator new(  
   size_t count  
);  
void *__cdecl operator new(  
   size_t count,   
   void * object  
) throw();  
void *__cdecl operator new(  
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
 `operator new`的是新的純量表單，與新的向量表單\([new&#91;&#93; 運算子](../c-runtime-library/new-operator-crt.md)\)。  
  
 第一種形式的運算子稱為無放置 \(nonplacement\) 形式。  這個運算子的第二分表單稱為placement 表單，而這個運算子第三種形式是 nonthrowing，placement表單。  
  
 運算子的第一個形式是由編譯器定義的，而且不需要 new.h 包括在您的程式中。  
  
 [刪除運算子](../c-runtime-library/operator-delete-crt.md) 以利用`operator new`釋放被配置的記憶體 。  
  
 您可以設定新運算子的傳回值為 NULL 或在失敗時擲回的例外狀況。  如需詳細資訊，請參閱新的 [新增與移除運算子](../cpp/new-and-delete-operators.md) 。  
  
 加上了擲回的或無擲回例外的行為後， CRT  `operator new` 則與在 Standard C\+\+ 程式庫中的[operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md)行為相同。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**new**|\<new.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 下列範例顯示如何使用純量， `operator new`的 nonplacement 表單。  
  
```  
// crt_new1.cpp  
#include <stdio.h>  
int main() {  
   int * i = new int(6);  
   printf("%d\n", *i);  
   delete i;  
}  
```  
  
 下列範例顯示如何使用純量， `operator new`的placement 表單。  
  
```  
// crt_new2.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * i = new int(12);  
   printf("*i = %d\n", *i);  
   // initialize existing memory (i) with, in this case, int(7)  
   int * j = new(i) int(7);   // placement new  
   printf("*j = %d\n", *j);  
   printf("*i = %d\n", *i);  
   delete i;   // or, could have deleted j  
}  
```  
  
 下列範例顯示如何使用純量， `operator new`的 placement，不擲回表單。  
  
```  
// crt_new3.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   // allocates memory, initialize (8) and if call fails, new returns null  
   int * k = new(std::nothrow) int(8);   // placement new  
   printf("%d\n", *k);  
   delete k;  
}  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../c-runtime-library/memory-allocation.md)