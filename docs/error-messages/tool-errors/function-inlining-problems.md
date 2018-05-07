---
title: 函式內嵌問題 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 670136a61d5991655a5d99e8257c6bcc907f2dfb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="function-inlining-problems"></a>函式內嵌問題
如果您使用內嵌函式，您必須：  
  
-   有您所包含的標頭檔中實作的內嵌函式。  
  
-   具有內嵌開啟標頭檔中。  
  
```  
// LNK2019_function_inline.cpp  
// compile with: /c   
// post-build command: lib LNK2019_function_inline.obj  
#include <stdio.h>  
struct _load_config_used {  
   void Test();  
   void Test2() { printf("in Test2\n"); }  
};  
  
void _load_config_used::Test() { printf("in Test\n"); }  
```  
  
 然後，  
  
```  
// LNK2019_function_inline_2.cpp  
// compile with: LNK2019_function_inline.lib  
struct _load_config_used {  
   void Test();  
   void Test2();  
};  
  
int main() {  
   _load_config_used x;  
   x.Test();  
   x.Test2();   // LNK2019  
}  
```  
  
 如果您使用`#pragma inline_depth`編譯器指示詞，請確定您已設定的值為 2 或更高。 零值將會關閉內嵌。 也請確定您使用 **/Ob1**或 **/Ob2**編譯器選項。  
  
 混用不同的模組上的內嵌和非內嵌編譯選項可能有時會造成問題。 C + + 程式庫會透過函式內嵌為開啟 ([/Ob1](../../build/reference/ob-inline-function-expansion.md)或[/Ob2](../../build/reference/ob-inline-function-expansion.md)) 但描述該函式對應的標頭檔案已關閉內嵌 （未選項），您會收到錯誤 LNK2001。 函式不會內嵌於程式碼的標頭檔，但因為它們不在程式庫檔案中沒有任何位址，解析參考。  
  
 同樣地，使用函式內嵌的專案尚未定義函式在.cpp 檔案，而非標頭中的檔案，也會取得 LNK2019。 標頭檔會包含所有位置適當，但函式僅內嵌時的.cpp 檔通過編譯器;因此，連結器會將函式視為其他模組中使用時，無法解析外部符號。  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 然後，  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 然後，  
  
```  
// LNK2019_FIP_2.cpp  
// compile with: LNK2019_FIP.cpp  
// LNK2019 expected  
#include "LNK2019_FIP.h"  
int main() {  
   testclass testclsObject;  
  
   // module cannot see the implementation of PublicStatMemFunc1  
   testclsObject.PublicStatMemFunc1();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)