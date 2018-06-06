---
title: __ptr32、 __ptr64 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5746c8f54a51e24bad23dcb66f6648266e2e4b56
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704811"
---
# <a name="ptr32-ptr64"></a>__ptr32、__ptr64

**Microsoft 專屬**

`__ptr32` 代表 32 位元系統上的原生指標，而 `__ptr64` 代表 64 位元系統上的原生指標。

下列範例將示範如何宣告每一個這些類型的指標：

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

 在 32 位元系統上，使用 `__ptr64` 宣告的指標會截斷為 32 位元指標。 在 64 位元系統上，使用 `__ptr32` 宣告的指標會強制轉型為 64 位元指標。

> [!NOTE]
> 您無法使用`__ptr32`或`__ptr64`編譯時 **/clr: pure**。 否則，會產生編譯器錯誤 C2472。 **/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

下列範例將示範如何使用 `__ptr32` 和 `__ptr64` 關鍵字宣告和配置指標。

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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

- [基本類型](../cpp/fundamental-types-cpp.md)