---
title: "編譯器警告 （層級 1） C4750 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
caps.latest.revision: 5
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
ms.sourcegitcommit: 84f0628de933344eb23dc6325679abdcd3699c3a
ms.openlocfilehash: 6e22ef89b92a5b584979abbd370f82b482cf74e0
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4750"></a>編譯器警告 (層級 1) C4750
'identifier': 函式中有 _alloca() 內嵌成迴圈  
  
 'Identifier' 函式會強制的內嵌展開[_alloca](../../c-runtime-library/reference/alloca.md)函式在迴圈內，迴圈執行時可能會造成堆疊溢位。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定 'identifier' 函式不會修改與[__forceinline](../../cpp/inline-functions-cpp.md)規範。  
  
2.  請確定 'identifier' 函式不包含[_alloca](../../c-runtime-library/reference/alloca.md)包含在迴圈中的函式。  
  
3.  未指定[/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/Ox](../../build/reference/ox-full-optimization.md)，或[/Og](../../build/reference/og-global-optimizations.md)編譯參數。  
  
4.  位置[_alloca](../../c-runtime-library/reference/alloca.md)函式中[嘗試-try-except 陳述式](../../cpp/try-except-statement.md)，將會攔截堆疊溢位。  
  
## <a name="example"></a>範例  
 下列程式碼範例會呼叫迴圈中的 `MyFunction` ，而 `MyFunction` 會呼叫 `_alloca` 函式。 `__forceinline` 修飾詞會造成 `_alloca` 函式的內嵌展開。  
  
```  
// c4750.cpp  
// compile with: /O2 /W1 /c  
#include <intrin.h>  
  
char * volatile newstr;  
  
__forceinline void myFunction(void) // C4750 warning  
{  
// The _alloca function does not require a __try/__except   
// block because the example uses compiler option /c.  
    newstr = (char * volatile) _alloca(1000);  
}  
  
int main(void)  
{  
    for (int i=0; i<50000; i++)  
       myFunction();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [_alloca](../../c-runtime-library/reference/alloca.md)
