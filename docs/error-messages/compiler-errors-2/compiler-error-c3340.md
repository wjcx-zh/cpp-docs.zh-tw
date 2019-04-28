---
title: 編譯器錯誤 C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: 1eff84ec133b55ddc3df98364c7d8542be398a69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300683"
---
# <a name="compiler-error-c3340"></a>編譯器錯誤 C3340

'interface': 在 coclass 'class' 中，介面不可以同時為 'restricted' 和 'default'

[受限制](../../windows/restricted.md) 屬性與 [預設](../../windows/default-cpp.md) 屬性互斥。

下列範例會產生 C3340：

```
// C3340.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   HRESULT f1();
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),
default(IMyIface),
source(IMyIface),restricted(IMyIface) ]
class CmyClass // C3340
{
};

int main()
{
}
```