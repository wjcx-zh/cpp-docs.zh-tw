---
title: novtable |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad0c50330d174a6139ce6e588b278e03cd99562
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942920"
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Microsoft 特定的  
 這是 **__declspec**擴充的屬性。  
  
 這種 **__declspec**可以套用至任何類別宣告，但應該只會套用至純介面類別，也就是將不會自行執行個體化的類別。 **__Declspec**讓編譯器產生建構函式和類別的解構函式中初始化 vfptr 的程式碼停止。 在大部分情況下，這樣只能移除與類別相關的 vtable 參考，因此連結器會將它移除。 使用這種 **__declspec**可能會導致大幅縮小程式碼大小。  
  
 如果您嘗試將標記為 `novtable` 的類別執行個體化，然後存取類別成員，您會收到存取違規 (AV)。  
  
## <a name="example"></a>範例  
  
```cpp 
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
```Output  
In Y  
```  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)