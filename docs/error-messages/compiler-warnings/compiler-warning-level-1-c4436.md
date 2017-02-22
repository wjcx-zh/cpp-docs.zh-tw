---
title: "編譯器警告 (層級 1) C4436 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# 編譯器警告 (層級 1) C4436
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

虛擬基底從 'class1' 到 'class2' 的 dynamic\_cast 在建構函式或解構函式中實際上可能無法與部分建構的物件以 \/vd2 編譯或定義 'class2' 與 \#pragma vtordisp \(2\)  
  
 編譯器遇到具有下列特性的 `dynamic_cast` 作業。  
  
-   轉換是從基底類別指標到衍生類別的指標。  
  
-   衍生的類別由基底類別進行虛擬繼承。  
  
-   衍生類別不具備虛擬基底的 `vtordisp` 欄位。  
  
-   在衍生類別的建構函式或解構函式中，或從衍生類別進一步繼承的一些類別中找到模型。  
  
 警告表示如果在部分建構的物件上作業，`dynamic_cast` 可能無法正確執行。如果衍生的建構函式\/解構函式在一些進階衍生物件的子物件上作業，就會發生這種情況。如果在警告的衍生類別名稱會是進一步衍生，警告可以忽略。  
  
## 範例  
 下列範例會產生 C4436 並示範從遺漏 `vtordisp` 欄位出現的程式碼產生問題。  
  
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
  
## 請參閱  
 [dynamic\_cast 運算子](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [編譯器警告 \(層級 4\) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)