---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: ccf544608bcba83af17702767562ef93d775b5a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227253"
---
# <a name="novtable"></a>novtable

**Microsoft 特定的**

這是 **`__declspec`** 擴充屬性。

這種形式的 **`__declspec`** 可以套用至任何類別宣告，但只能套用至純介面類別別，也就是永遠不會自行具現化的類別。 會 **`__declspec`** 阻止編譯器產生程式碼，以初始化函式中的 vfptr 和類別的析構函數。 在大部分情況下，這樣只能移除與類別相關的 vtable 參考，因此連結器會將它移除。 使用這種形式的 **`__declspec`** 可能會大幅減少程式碼大小。

如果您嘗試將標記為的類別具現化， **`novtable`** 然後再存取類別成員，您將會收到存取違規（AV）。

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

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[`__declspec`](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
