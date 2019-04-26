---
title: 編譯器錯誤 C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: 7ca84b4f054852aefa75a9c4547286137b436c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182479"
---
# <a name="compiler-error-c3247"></a>編譯器錯誤 C3247

'class1' : Coclass 無法繼承自其他 Coclass 'class2'

標記為 [coclass](../../windows/coclass.md) 屬性的類別無法繼承自另一個標記為 `coclass` 屬性的類別。

下列範例會產生 C3247：

```
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