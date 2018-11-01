---
title: 編譯器警告 （層級 4） C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 11307ddc3b13a9cd9b36f1ee927082104792b07f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648353"
---
# <a name="compiler-warning-level-4-c4457"></a>編譯器警告 （層級 4） C4457

> 宣告的 '*識別碼*' 會隱藏函式參數

Deklarace*識別碼*本機範圍內隱藏相同名稱的函式參數的宣告。 這項警告可讓您知道的參考*識別碼*在區域範圍中解析的區域宣告的版本，不會使用參數，這可能會或可能不到您的意圖。 若要修正此問題，我們建議您提供參數名稱與本機變數名稱，不會衝突。

## <a name="example"></a>範例

下列範例會產生 C4457，因為參數`x`和 區域變數`x`在`member_fn`有相同的名稱。 若要修正此問題，請使用不同的參數和區域變數的名稱。

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
