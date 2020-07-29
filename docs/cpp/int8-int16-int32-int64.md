---
title: __int8、__int16、__int32、__int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 7888a282fffbaa2a23783c3875e02838fd0b1826
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227396"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8、__int16、__int32、__int64

**Microsoft 特定**

Microsoft C/C++ 的功能支援可調整大小的整數類型。 您可以使用類型規範來宣告8、16、32或64位整數變數 **`__intN`** ，其中 ***`N`*** 是8、16、32或64。

下列範例為其中每個可調整大小整數類型宣告一個變數：

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

類型 **`__int8`** 、 **`__int16`** 和 **`__int32`** 是具有相同大小之 ANSI 類型的同義字，適用于撰寫可在多個平臺上進行相同行為的可移植程式碼。 **`__int8`** 資料類型與類型同義，與 **`char`** 類型同義，而且與 **`__int16`** **`short`** **`__int32`** 類型同義 **`int`** 。 **`__int64`** 類型與類型同義 **`long long`** 。

為了與舊版相容，、、和為 **`_int8`** **`_int16`** **`_int32`** **`_int64`** **`__int8`** 、、和的同義字 **`__int16`** ， **`__int32`** **`__int64`** 除非指定了編譯器選項[ `/Za` \( 停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="example"></a>範例

下列範例顯示 `__intN` 參數會升級為 **`int`** ：

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[內建類型](../cpp/fundamental-types-cpp.md)<br/>
[資料類型範圍](../cpp/data-type-ranges.md)<br/>
