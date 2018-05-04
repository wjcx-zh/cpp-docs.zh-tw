---
title: 使用陣列 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c2140dbe786a5d2a2a1b86eca17912e5e06b922
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="using-arrays-c"></a>使用陣列 (C++)
使用陣列註標運算子 (`[ ]`)，您可以存取陣列的個別項目。 如果一維陣列用於沒有註標的運算式，陣列名稱判斷值為陣列中第一個項目的指標。  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 當您使用多維陣列時，您可以在運算式中使用各種組合。  
  
```  
// using_arrays_2.cpp  
// compile with: /EHsc /W1  
#include <iostream>  
using namespace std;  
int main() {  
   double multi[4][4][3];   // Declare the array.  
   double (*p2multi)[3];  
   double (*p1multi);  
  
   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.  
   p2multi = multi[3];               // Make p2multi point to  
                                     // fourth "plane" of multi.  
   p1multi = multi[3][2];            // Make p1multi point to  
                                     // fourth plane, third row  
                                     // of multi.  
}  
```  
  
 在上述程式碼中，`multi` 是 `double` 類型的三維陣列。 `p2multi` 指標指向大小為三的 `double` 類型陣列。 在此範例中，陣列搭配使用的註標有一個、兩個和三個。 雖然更常見的是指定所有註標 (如在 `cout` 陳述式中)，但有時選取陣列元素的特定子集是很有用的 (如 `cout` 之後的陳述式所示)。  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../cpp/arrays-cpp.md)