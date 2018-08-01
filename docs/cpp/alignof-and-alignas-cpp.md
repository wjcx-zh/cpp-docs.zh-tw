---
title: alignof 和 alignas （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c10821f7e71c928fa749c2b85bd076cb9af6d04a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402412"
---
# <a name="alignof-and-alignas-c"></a>alignof 和 alignas (C++)
**Alignas**類型規範，以指定的變數和使用者定義類型的自訂對齊方式的可攜性，c + + 標準方式。 **Alignof**運算子同樣是標準的可移植的方式，來取得指定的類型或變數的對齊方式。  
  
## <a name="example"></a>範例  
 您可以使用**alignas**對類別、 結構或等位，或個別成員。 當多個**alignas**遇到規範時，編譯器會選擇最嚴格的一個 （最大值）。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [對齊](../cpp/alignment-cpp-declarations.md)