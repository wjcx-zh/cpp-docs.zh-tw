---
title: "alignof 和 alignas （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a506a3c44c3304e786c41a2eb049939d317778e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="alignof-and-alignas-c"></a>alignof 和 alignas (C++)
`alignas` 類型規範是可攜性的 C++ 標準方式，用來指定變數和使用者定義類型的自訂對齊方式。 `alignof` 運算子同樣是標準的可攜性方式，用來取得指定類型或變數的對齊方式。  
  
## <a name="example"></a>範例  
 您可以對類別、結構或等位，或個別成員使用 `alignas`。 當遇到多個 `alignas` 規範時，編譯器會選擇最嚴格的一個 (具有最大值者)。  
  
```cpp  
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  

int main()
{  
    std::cout << alignof(Bar) << std::endl; // output: 16  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [對齊](../cpp/alignment-cpp-declarations.md)