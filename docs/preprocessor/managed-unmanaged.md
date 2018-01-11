---
title: "managed、 unmanaged |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
dev_langs: C++
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d8e2b50f7d505a4e262559b6cb69b0bab81ffcd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="managed-unmanaged"></a>managed、unmanaged
啟用函式層級控制項，用於編譯 Managed 或 Unmanaged 的函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
      #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## <a name="remarks"></a>備註  
 [/Clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項提供模組層級的控制項，用於編譯 managed 或 unmanaged 的函式。  
  
 編譯 Unmanaged 函式用於原生平台，Common Language Runtime 會將該部分的程式執行傳遞至該原生平台。  
  
 函式會編譯為 managed 預設時**/clr**用。  
  
 套用這些 pragma 時：  
  
-   將 pragma 新增到函式之前而不是函式主體之內。  
  
-   將 pragma 新增到 `#include` 陳述式之後。 請勿在 `#include` 陳述式之前使用這些 pragma。  
  
 編譯器會忽略`managed`和`unmanaged`pragma 如果**/clr**不是在編譯中。  
  
 具現化樣板函式時，定義樣板時的 pragma 狀態決定函式為 Managed 或 Unmanaged 函式。  
  
 如需詳細資訊，請參閱[初始化的混合的組件](../dotnet/initialization-of-mixed-assemblies.md)。  
  
## <a name="example"></a>範例  
  
```cpp  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
```Output  
In managed function.  
In unmanaged function.  
```  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)