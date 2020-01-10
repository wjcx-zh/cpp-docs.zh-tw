---
title: 編譯器錯誤 C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 6faf035c0f4f68b10b187c56bea4cafc776998cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757952"
---
# <a name="compiler-error-c3707"></a>編譯器錯誤 C3707

' function '：分配介面方法必須有 dispid

如果您使用 `dispinterface` 方法，則必須將 `dispid`指派給它。 若要修正這個錯誤，請將 `dispid` 指派給 `dispinterface` 方法，例如，藉由在下列範例中的方法上取消批註 `id` 屬性。 如需詳細資訊，請參閱屬性分配[介面](../../windows/dispinterface.md)和[識別碼](../../windows/id.md)。

下列範例會產生 C3707：

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
