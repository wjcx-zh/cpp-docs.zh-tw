---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: a147af8f536923082df3a2d6d332150a57d6af1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857381"
---
# <a name="novtable"></a>novtable

**Microsoft 專屬**

這是 **__declspec**的擴充屬性。

這種形式的 **__declspec**可以套用至任何類別宣告，但只能套用至純介面類別別，也就是永遠不會自行具現化的類別。 **__Declspec**會阻止編譯器產生程式碼，以初始化函式中的 vfptr 和類別的析構函數。 在大部分情況下，這樣只能移除與類別相關的 vtable 參考，因此連結器會將它移除。 使用這種形式的 **__declspec**可能會導致程式碼大小大幅降低。

如果您嘗試具現化以**novtable**標記的類別，然後再存取類別成員，您將會收到存取違規（AV）。

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

## <a name="see-also"></a>請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)