---
title: 編譯器錯誤 C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 8a1525539c84ea427815a03057bb6d2f9213fec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431105"
---
# <a name="compiler-error-c3707"></a>編譯器錯誤 C3707

'function': dispinterface 方法必須有 dispid

如果您使用`dispinterface`方法中，您必須將它指派`dispid`。 若要修正這個錯誤，請指派`dispid`要`dispinterface`方法，例如，取消註解`id`在下列範例中的方法上的屬性。 如需詳細資訊，請參閱屬性[dispinterface](../../windows/dispinterface.md)並[識別碼](../../windows/id.md)。

下列範例會產生 C3707:

```
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