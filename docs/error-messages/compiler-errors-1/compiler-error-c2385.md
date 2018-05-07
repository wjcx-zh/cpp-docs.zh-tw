---
title: 編譯器錯誤 C2385 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2385
dev_langs:
- C++
helpviewer_keywords:
- C2385
ms.assetid: 6d3dd1f2-e56d-49d7-865c-6a9acdb17417
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc152cd9d83b163632e64d1e2d8a0c5692439987
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2385"></a>編譯器錯誤 C2385
模稜兩可的 'member' 的存取權  
  
 成員可以衍生自多個物件 （它繼承自多個物件）。  若要解決這個錯誤，  
  
-   提供型別轉換，讓成員模稜兩可。  
  
-   重新命名在基底類別模稜兩可的成員。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2385。  
  
```  
// C2385.cpp  
// C2385 expected  
#include <stdio.h>  
  
struct A   
{  
    void x(int i)   
    {  
        printf_s("\nIn A::x");  
    }  
};  
  
struct B   
{  
    void x(char c)   
    {  
        printf_s("\nIn B::x");  
    }  
};  
  
// Delete the following line to resolve.  
struct C : A, B {}  
  
// Uncomment the following 4 lines to resolve.  
// struct C : A, B   
// {  
//     using B::x;  
//     using A::x;  
// };  
  
int main()   
{  
    C aC;  
    aC.x(100);  
    aC.x('c');  
}  
  
struct C : A, B   
{  
    using B::x;  
    using A::x;  
};  
```