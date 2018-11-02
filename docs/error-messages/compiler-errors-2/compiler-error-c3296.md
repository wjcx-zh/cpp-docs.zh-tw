---
title: 編譯器錯誤 C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: 2e9787b063a5a37af8d0e0fdd04492a743792646
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588106"
---
# <a name="compiler-error-c3296"></a>編譯器錯誤 C3296

'property': 已經有這個名稱的屬性

編譯器遇到具有相同名稱的多個屬性。 類型中的每個屬性都必須具有唯一的名稱。

如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3296。

```
// C3296.cpp
// compile with: /clr /c
using namespace System;

ref class R {
public:
   property int MyProp[int] { int get(int); }

   property String^ MyProp[int] { void set(int, String^); }   // C3296
};
```