---
title: 編譯器警告 （層級 3） C4995 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4995
dev_langs:
- C++
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6bf1bbab4ee9a5a08a1376c91c6a7bba160625
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4995"></a>編譯器警告 （層級 3） C4995
'function': 名稱被標示為已被取代的 #pragma  
  
 編譯器遇到函式已標記使用 pragma[取代](../../preprocessor/deprecated-c-cpp.md)。 未來的版本可能不再支援此函式。 您可以關閉此警告，與[警告](../../preprocessor/warning.md)pragma （下面的範例）。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4995:  
  
```  
// C4995.cpp  
// compile with: /W3  
#include <stdio.h>  
  
// #pragma warning(disable : 4995)  
void func1(void)  
{  
    printf("\nIn func1");  
}  
  
int main()   
{  
    func1();  
    #pragma deprecated(func1)  
    func1();   // C4995  
}  
```