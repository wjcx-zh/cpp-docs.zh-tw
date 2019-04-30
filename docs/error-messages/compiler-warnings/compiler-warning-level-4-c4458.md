---
title: 編譯器警告 （層級 4） C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: 9e5eb8dc44968332abc097bfbd16b48e3240695c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391448"
---
# <a name="compiler-warning-level-4-c4458"></a>編譯器警告 （層級 4） C4458

> 宣告的 '*識別碼*' 會隱藏類別成員

Deklarace*識別碼*本機範圍內隱藏相同名稱的宣告*識別項*在類別範圍。 這項警告可讓您知道的參考*識別碼*在這個範圍中解析本機宣告的版本，而不是類別成員版本，這可能會或可能不到您的意圖。 若要修正此問題，我們建議您提供與類別成員名稱的區域變數名稱，不會衝突。

## <a name="example"></a>範例

下列範例會產生 C4458，因為參數`x`和 區域變數`y`在`member_fn`類別中有相同的資料成員名稱。 若要修正此問題，請使用不同的參數和區域變數的名稱。

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
