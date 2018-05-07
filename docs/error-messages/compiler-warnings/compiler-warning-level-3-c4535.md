---
title: 編譯器警告 （層級 3） C4535 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4535
dev_langs:
- C++
helpviewer_keywords:
- C4535
ms.assetid: 2c5ad1aa-2558-41d1-8f06-47fef74c8d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97a505b715596a8c7e72264a59ef7c5913f4958c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4535"></a>編譯器警告 (層級 3) C4535
呼叫 _set_se_translator() 需要 /EHa  
  
 使用[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)需要[/EHa](../../build/reference/eh-exception-handling-model.md)編譯器選項而非 **/EHs**。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4535。  
  
```  
// C4535.cpp  
// compile with: /W3 /EHsc /c  
// C4535 expected  
// to fix, compile with /EHa instead  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
void SEFunc();  
void trans_func( unsigned int, EXCEPTION_POINTERS* );  
  
class SE_Exception {  
private:  
   unsigned int nSE;  
public:  
   SE_Exception() {}  
   SE_Exception( unsigned int n ) : nSE( n ) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() { return nSE; }  
};  
  
int main() {  
   try {  
      _set_se_translator( trans_func );  
      SEFunc();  
   }  
   catch( SE_Exception e ) {  
      printf_s( "Caught a __try exception with SE_Exception.\n" );  
   }  
}  
  
void SEFunc() {  
   __try {  
      int x, y=0;  
      x = 5 / y;  
   }  
   __finally {  
      printf_s( "In finally\n" );  
   }  
}  
  
void trans_func( unsigned int u, EXCEPTION_POINTERS* pExp ) {  
   printf_s( "In trans_func.\n" );  
   throw SE_Exception();  
}  
```