---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: 9dcca6ec07a19d53da238020805299b652cbf919
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245150"
---
# <a name="novtable"></a>novtable

## <a name="microsoft-specific"></a>Microsoft 特定的

這是 **__declspec**擴充的屬性。

這種 **__declspec**可以套用至任何類別宣告，但應該只會套用至純介面類別，也就是將不會自行執行個體化的類別。 **__Declspec**讓編譯器產生建構函式和類別的解構函式中初始化 vfptr 的程式碼停止。 在大部分情況下，這樣只能移除與類別相關的 vtable 參考，因此連結器會將它移除。 使用這種 **__declspec**可能會導致大幅縮小程式碼大小。

如果您嘗試具現化類別，以標示**novtable**然後存取類別成員，您會收到存取違規 (AV)。

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

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)