---
title: 編譯器警告 (層級 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 84c6e8d09495d871b8c490a92558aaba14b0574c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185330"
---
# <a name="compiler-warning-level-4-c4437"></a>編譯器警告 (層級 4) C4437

在某些使用/vd2 編譯的內容中，從虛擬基底 ' class1 ' 到 ' class2 ' 的 dynamic_cast 可能會失敗，或定義具有 #pragma vtordisp （2）效果的 ' class2 '

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

編譯器遇到具有下列特性的 `dynamic_cast` 作業。

- 轉換是從基底類別指標到衍生類別指標。

- 衍生類別虛擬繼承基底類別。

- 衍生類別沒有虛擬基底的 `vtordisp` 欄位。

- 在衍生類別的函式或析構函數中找不到轉換，或從衍生類別進一步繼承的某個類別（否則會發出編譯器警告 C4436）。

此警告表示，如果 `dynamic_cast` 在部分結構化的物件上操作，則可能無法正確執行。  當從繼承在警告中命名的衍生類別之類別的函式或析構函數中呼叫封入函數時，就會發生這種情況。  如果警告中所命名的衍生類別永遠不會進一步衍生，或在物件結構或損毀期間未呼叫封入函式，則可以忽略此警告。

## <a name="example"></a>範例

下列範例會產生 C4437，並示範從遺漏的 `vtordisp` 欄位引發的程式碼產生問題。

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

## <a name="see-also"></a>另請參閱

[dynamic_cast 運算子](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[編譯器警告 (層級 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)
