---
title: 編譯器錯誤 C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: a09bf080c72e154a37cec5cdb75e714c12dd7150
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507977"
---
# <a name="compiler-error-c3707"></a>編譯器錯誤 C3707

' function '：分配介面方法必須有 dispid

如果您使用 `dispinterface` 方法，您必須將它指派給它 `dispid` 。 若要修正這個錯誤，請將指派給 `dispid` `dispinterface` 方法，例如， `id` 在下列範例中取消批註方法上的屬性。 如需詳細資訊，請參閱屬性 [介面介面](../../windows/attributes/dispinterface.md) 和 [識別碼](../../windows/attributes/id.md)。

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
