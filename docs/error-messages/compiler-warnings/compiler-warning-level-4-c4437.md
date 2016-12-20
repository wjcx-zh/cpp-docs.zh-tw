---
title: "編譯器警告 (層級 4) C4437 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4437
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dynamic\_cast從虛擬基底 'class1' 到 'class2' 實際上無法從內容中失敗以 \/vd2 編譯或定義 'class2' 與 \#pragma vtordisp \(2\)  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 編譯器遇到具有下列特性的 `dynamic_cast` 作業。  
  
-   轉換是從基底類別指標到衍生類別的指標。  
  
-   衍生的類別由基底類別進行虛擬繼承。  
  
-   衍生類別不具備虛擬基底的 `vtordisp` 欄位。  
  
-   轉型為衍生類別的建構函式或解構函式中找不到，否則衍生類別進一步繼承的一些類別 \(否則，編譯器警告 C4436 將發行\)。  
  
 警告表示如果在部分建構的物件上作業，`dynamic_cast` 可能無法正確執行。發生這種情況，當封入函式從繼承衍生類別在警告中名為類別的建構函式或解構函式時呼叫。如果在警告中名為的衍生類別會是進一步衍生或封入函式未在物件建構或解構時呼叫，警告可以忽略。  
  
## 範例  
 下列範例會產生 C4437 並示範從遺漏 `vtordisp` 欄位出現的程式碼產生問題。  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
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
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
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
 [編譯器警告 \(層級 1\) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)