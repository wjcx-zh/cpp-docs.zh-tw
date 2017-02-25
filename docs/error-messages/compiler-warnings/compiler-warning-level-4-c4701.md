---
title: "編譯器警告 (層級 4) C4701 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4701"
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器警告 (層級 4) C4701
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可能是未初始化的區域變數" name "  
  
 區域變數 *name* 可能已經使用了，不會指派值。  這會導致不可預測的結果。  
  
## 範例  
 下列程式碼會產生 C4701 and C4703。  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
  **c:\\src\\test.cpp \(10\)：警告的 C4701:可能是'p'使用的未初始化的區域變數**  
 **c:\\src\\test.cpp \(10\)：警告的 C4703：可能是'p'使用的未初始化的區域指標變數** 若要更正這則警告，請將變數初始化，如此範例所示：  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## 請參閱  
 [編譯器警告 \(層級 4\) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)   
 [警告， \/sdl 和改善未初始化的變數偵測](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)