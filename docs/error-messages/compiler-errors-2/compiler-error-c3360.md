---
title: 編譯器錯誤 C3360
ms.date: 11/04/2016
f1_keywords:
- C3360
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
ms.openlocfilehash: 5ac496d8ad981a8e36c7b69e73a42a1e1d2e214d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504709"
---
# <a name="compiler-error-c3360"></a>編譯器錯誤 C3360

'string': 無法建立名稱

傳遞給 [uuid](../../windows/attributes/uuid-cpp-attributes.md) 屬性的值無效。

下列範例會產生 C3360：

```cpp
// C3360.cpp
[ uuid("1") ]
// try this line instead
// [ uuid("12341234-1234-1234-1234-123412341234") ]
struct A   // C3360
{
};

int main()
{
}
```
