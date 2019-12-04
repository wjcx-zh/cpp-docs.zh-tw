---
title: 編譯器錯誤 C3373
ms.date: 11/04/2016
f1_keywords:
- C3373
helpviewer_keywords:
- C3373
ms.assetid: 6e7586c3-1a15-4773-ad20-f90090a400dc
ms.openlocfilehash: cbf6b19e6ae5e5278d7536ba8ec1cfc28483f753
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758576"
---
# <a name="compiler-error-c3373"></a>編譯器錯誤 C3373

屬性 'attribute' 除了在 coclass 中以外，不需要任何引數

部分屬性可以套用至多個 C++ 建構，但該屬性的部分引數只能用在部分建構上。

下列範例會產生 C3373：

```cpp
// C3373.cpp
#include <windows.h>

[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   // arguments to source and restricted are not allowed when
   // these attributes are applied to an interface
   [source(IMyIface)] HRESULT f1();
   [restricted(IMyIface)] HRESULT f2(); // C3373
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f) ]
class CMyClass : public IMyIface {
};

int main() {
}
```
