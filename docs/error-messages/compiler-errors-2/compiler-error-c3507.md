---
title: 編譯器錯誤 C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: a38efcc0d74bbea0e0bf767cb9e5a11561ab4fb8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507121"
---
# <a name="compiler-error-c3507"></a>編譯器錯誤 C3507

ProgID 不能超過39個字元的 ' id ';也不包含 '. ' 以外的任何標點符號;也不能以數位開頭

[Progid](../../windows/attributes/progid.md)屬性對其所能採用的值有所限制。

下列範例會產生 C3507：

```cpp
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```
