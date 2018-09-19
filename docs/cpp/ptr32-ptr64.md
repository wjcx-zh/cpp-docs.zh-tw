---
title: __ptr32，__ptr64 |Microsoft Docs
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
ms.openlocfilehash: 573af4088e288403edaa8e5c34fb84817442c8f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115992"
---
# <a name="ptr32-ptr64"></a>__ptr32、__ptr64

**Microsoft 專屬**

**__ptr32**代表原生指標在 32 位元系統上，雖然 **__ptr64**代表 64 位元系統上的原生指標。

下列範例將示範如何宣告每一個這些類型的指標：

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

在 32 位元系統上，指標使用的宣告 **__ptr64**截斷為 32 位元指標。 在 64 位元系統上，指標使用的宣告 **__ptr32**會強制轉型為 64 位元指標。

> [!NOTE]
> 您無法使用 **__ptr32**或是 **__ptr64**進行編譯時 **/clr: pure**。 否則，會產生編譯器錯誤 C2472。 **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

下列範例示範如何宣告和配置與指標 **__ptr32**並 **__ptr64**關鍵字。

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

[基本類型](../cpp/fundamental-types-cpp.md)