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
ms.openlocfilehash: c3ebe642284c6ee269dbfc39985630b7d949435f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179207"
---
# <a name="__ptr32-__ptr64"></a>__ptr32、__ptr64

**Microsoft 專屬**

**__ptr32**代表32位系統上的原生指標，而 **__ptr64**代表64位系統上的原生指標。

下列範例將示範如何宣告每一個這些類型的指標：

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

在32位系統上，使用 **__ptr64**宣告的指標會被截斷為32位指標。 在64位系統上，使用 **__ptr32**宣告的指標會強制轉型為64位指標。

> [!NOTE]
> 使用 **/clr： pure**進行編譯時，您無法使用 **__ptr32**或 **__ptr64** 。 否則，將會產生編譯器錯誤 C2472。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_ptr32**和 **_ptr64**就是 **__ptr32**和 **__ptr64**的同義字。

## <a name="example"></a>範例

下列範例顯示如何使用 **__ptr32**和 **__ptr64**關鍵字來宣告和配置指標。

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[內建類型](../cpp/fundamental-types-cpp.md)
