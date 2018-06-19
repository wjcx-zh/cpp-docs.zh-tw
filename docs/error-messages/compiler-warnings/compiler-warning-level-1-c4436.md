---
title: 編譯器警告 （層級 1） C4436 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1da06a329a9c0bdfcff6877ce69c8e3672619bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281638"
---
# <a name="compiler-warning-level-1-c4436"></a>編譯器警告 (層級 1) C4436
建構函式或解構函式中從虛擬基底 'class1' 到 'class2' 的 dynamic_cast 在使用部分建構的物件時可能會失敗        使用 /vd2 編譯，或在 #pragma vtordisp(2) 有效的情況下定義 'class2'  
  
 編譯器遇到具有下列特性的 `dynamic_cast` 作業。  
  
-   轉換是從基底類別指標到衍生類別指標。  
  
-   衍生類別虛擬繼承基底類別。  
  
-   衍生類別沒有虛擬基底的 `vtordisp` 欄位。  
  
-   在衍生類別 (或從衍生類別進一步繼承的特定類別) 的建構函式或解構函式中找到轉換。  
  
 警告表示如果在部分建構的物件上作業，`dynamic_cast` 可能無法正確執行。  如果衍生的建構函式/解構函式在進一步衍生物件的子物件上作業，就會發生這種情況。  如果在警告中指名的衍生類別絕不是進一步衍生，警告可以忽略。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4436 並示範從遺漏的 `vtordisp` 欄位中出現的程式碼產生問題。  
  
```cpp  
// C4436.cpp  
// To see the warning and runtime assert, compile with: /W1  
// To eliminate the warning and assert, compile with: /W1 /vd2  
//       or compile with: /W1 /DFIX  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4436  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [dynamic_cast 運算子](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [編譯器警告 (層級 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)