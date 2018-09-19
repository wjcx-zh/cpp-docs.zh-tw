---
title: 編譯器警告 （層級 4） C4437 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11d234f7f264f051042ae99900875b8e570fa66a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118637"
---
# <a name="compiler-warning-level-4-c4437"></a>編譯器警告 (層級 4) C4437

從虛擬基底 'class1' 到 'class2' 的 dynamic_cast 無法使用/vd2 某些內容編譯會失敗，或在定義 'class2' #pragma vtordisp(2)

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

編譯器遇到具有下列特性的 `dynamic_cast` 作業。

- 轉換是從基底類別指標到衍生類別指標。

- 衍生類別虛擬繼承基底類別。

- 衍生類別沒有虛擬基底的 `vtordisp` 欄位。

- 在建構函式或解構函式的衍生類別中，找不到轉換或某些類別進一步繼承自衍生類別 （否則編譯器警告將發出 C4436）。

警告表示`dynamic_cast`當它在部分建構的物件上操作時，即可能不執行。  封入函式呼叫建構函式或解構函式之類別的繼承警告中指名的衍生的類別時，就會發生這種情況。  如果警告中指名的衍生的類別絕不是進一步衍生，或封入函式不會呼叫物件建構或解構期間，您可以忽略此警告。

## <a name="example"></a>範例

下列範例會產生 C4437，並示範從遺漏程式碼產生問題`vtordisp`欄位。

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