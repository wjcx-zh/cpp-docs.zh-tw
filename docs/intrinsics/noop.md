---
title: __noop | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __noop_cpp
- __noop
dev_langs:
- C++
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ed6228d145261edc323ca0f90899e42dcf02f46
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="noop"></a>__noop
**Microsoft 特定的**  
  
 `__noop`內建函式指定應該忽略的函式和剖析引數清單，但卻沒有程式碼產生的引數。 它適用於不接受引數數目可變的全域偵錯函式中。  
  
 編譯器會將轉換`__noop`設為 0，在編譯時期內建函式。  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用`__noop`。  
  
```  
// compiler_intrinsics__noop.cpp  
// compile with or without /DDEBUG  
#include <stdio.h>  
  
#if DEBUG  
   #define PRINT   printf_s  
#else  
   #define PRINT   __noop  
#endif  
  
int main() {  
   PRINT("\nhello\n");  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)