---
title: "編譯器警告 (層級 4) C4703 | Microsoft Docs"
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
  - "C4703"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4703"
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4703
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可能使用未初始化區域指標變數 'name'。  
  
 區域指標變數 *name* 可能在沒有指派值的情況下已經使用了。  這會導致不可預測的結果。  
  
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
 [編譯器警告 \(層級 4\) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)   
 [警告， \/sdl 和改善未初始化的變數偵測](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)