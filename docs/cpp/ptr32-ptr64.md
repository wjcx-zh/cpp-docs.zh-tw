---
title: __ptr32、__ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: 5ff2fa22c8a466252cfaf8b80dc8d56774aff58e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227149"
---
# <a name="__ptr32-__ptr64"></a>__ptr32、__ptr64

**Microsoft 特定的**

**`__ptr32`** 表示32位系統上的原生指標，而 **`__ptr64`** 表示64位系統上的原生指標。

下列範例將示範如何宣告每一個這些類型的指標：

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

在32位系統上，使用宣告的指標 **`__ptr64`** 會被截斷為32位指標。 在64位系統上，使用宣告的指標 **`__ptr32`** 會強制轉型為64位指標。

> [!NOTE]
> 使用 **`__ptr32`** **`__ptr64`** **/clr： pure**進行編譯時，您無法使用或。 否則，將會產生編譯器錯誤 C2472。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

為了與舊版相容， **_ptr32**和 **_ptr64**都是和的同義字， **`__ptr32`** **`__ptr64`** 除非指定了編譯器選項[/za 停用 \( 語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="example"></a>範例

下列範例顯示如何使用和關鍵字宣告和配置指標 **`__ptr32`** **`__ptr64`** 。

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內建類型](../cpp/fundamental-types-cpp.md)
