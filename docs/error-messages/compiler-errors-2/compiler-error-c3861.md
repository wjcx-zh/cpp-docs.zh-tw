---
title: "編譯器錯誤 C3861 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3861
dev_langs:
- C++
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 177890dcd3ff2abf07f5d9e282efd4a9fd7121a7
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3861"></a>編譯器錯誤 C3861
'identifier'：找不到識別項  
  
即使使用引數相依查閱，編譯器仍無法解析識別項的參考。  
  
若要修正此錯誤，請檢查識別項宣告的大小寫和拼字。 確認[範圍解析運算子](../../cpp/scope-resolution-operator.md)和命名空間[using 指示詞](../../cpp/namespaces-cpp.md#using_directives)正確使用。 如果標頭檔中已宣告識別項，請確認在參考標頭之前，是否已將其包含在內。 另請檢查識別項不所排除[條件式編譯指示詞](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3861。  
  
```cpp  
// C3861.cpp  
void f2(){}  
int main() {  
   f();   // C3861  
   f2();   // OK  
}  
```  
  
## <a name="example"></a>範例  
C++ 標準程式庫中的 Exception 類別現在會出現在 `std` 命名空間中。  
  
```cpp  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```
