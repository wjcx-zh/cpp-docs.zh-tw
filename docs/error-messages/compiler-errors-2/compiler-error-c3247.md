---
title: 編譯器錯誤 C3247 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3247
dev_langs:
- C++
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f706b4f1a1935a5c6246ea285c7e8b2b746f08cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047235"
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