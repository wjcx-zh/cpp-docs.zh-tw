---
title: "__ptr32、 __ptr64 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs: C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3e811999bacada521d77bc14b19eb86d660b5901
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ptr32-ptr64"></a>__ptr32、__ptr64
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__ptr32` 代表 32 位元系統上的原生指標，而 `__ptr64` 代表 64 位元系統上的原生指標。  
  
 下列範例將示範如何宣告每一個這些類型的指標：  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 在 32 位元系統上，使用 `__ptr64` 宣告的指標會截斷為 32 位元指標。 在 64 位元系統上，使用 `__ptr32` 宣告的指標會強制轉型為 64 位元指標。  
  
> [!NOTE]
>  您無法使用`__ptr32`或`__ptr64`編譯時**/clr: pure**。 否則會產生 `Compiler Error C2472`。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
## <a name="example"></a>範例  
 下列範例將示範如何使用 `__ptr32` 和 `__ptr64` 關鍵字宣告和配置指標。  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
```Output  
32  
64  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [基本類型](../cpp/fundamental-types-cpp.md)