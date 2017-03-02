---
title: "編譯器警告 （層級 4） C4703 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4703
dev_langs:
- C++
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 75aa17d24abfad3eec3bc74f82218af6ceedadec
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4703"></a>編譯器警告 (層級 4) C4703
已使用可能未初始化的本機指標變數 'name'  
  
 本機指標變數*名稱*可能會指派值的情況下使用。 這可能導致無法預期的結果。  
  
## <a name="example"></a>範例  
 下列程式碼會產生 C4701 和 C4703。  
  
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
  
```Output  
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used  
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used  
  
```  
  
 若要更正這則警告，請將變數初始化，如這個範例所示：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [編譯器警告 （層級 4） C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)   
 [警告、 /sdl 和改善未初始化的變數偵測](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)
