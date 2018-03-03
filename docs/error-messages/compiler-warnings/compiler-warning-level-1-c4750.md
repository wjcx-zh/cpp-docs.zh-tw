---
title: "編譯器警告 （層級 1） C4750 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e1c880e07a56be1dd7b8c82f5e6f0473ededdd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4750"></a>編譯器警告 (層級 1) C4750
'identifier': 函式中有 _alloca() 內嵌成迴圈  
  
 'identifier' 函式會強制 [_alloca](../../c-runtime-library/reference/alloca.md) 函式在迴圈中內嵌展開，而可能在執行迴圈時造成堆疊溢位。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  確定未使用 [__forceinline](../../cpp/inline-functions-cpp.md) 規範修改 'identifier' 函式。  
  
2.  確定 'identifier' 函式不包含內嵌於迴圈中的 [_alloca](../../c-runtime-library/reference/alloca.md) 函式。  
  
3.  不要指定 [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)、 [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)、 [/Ox](../../build/reference/ox-full-optimization.md)或 [/Og](../../build/reference/og-global-optimizations.md) 編譯參數。  
  
4.  將 [_alloca](../../c-runtime-library/reference/alloca.md) 函式放在會攔截堆疊溢位的 [try-except 陳述式](../../cpp/try-except-statement.md) 中。  
  
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
  
## <a name="see-also"></a>請參閱  
 [_alloca](../../c-runtime-library/reference/alloca.md)