---
title: 編譯器錯誤 C3707 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d18d4a82d06018cdba6147ba6756b1718648847a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052776"
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