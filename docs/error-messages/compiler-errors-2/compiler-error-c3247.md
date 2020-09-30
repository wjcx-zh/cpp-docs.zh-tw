---
title: 編譯器錯誤 C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: c1b8aaddac32af4e0936ce7d45fbc59c3835dda2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501390"
---
# <a name="compiler-error-c3247"></a>編譯器錯誤 C3247

'class1' : Coclass 無法繼承自其他 Coclass 'class2'

標記為 [coclass](../../windows/attributes/coclass.md) 屬性的類別無法繼承自另一個標記為 `coclass` 屬性的類別。

下列範例會產生 C3247：

```cpp
// C3247.cpp
[module(name="MyLib")];
[coclass]
class a {
};

[coclass]
class b : public a {   // C3247
};
int main() {
}
```
