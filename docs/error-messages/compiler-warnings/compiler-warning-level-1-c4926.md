---
title: 編譯器警告 (層級 1) C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: 839d0b8ffad947e7031ca618b255588f54b82770
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50634898"
---
# <a name="compiler-warning-level-1-c4926"></a>編譯器警告 (層級 1) C4926

'identifier': 已定義符號：忽略屬性

找到向前宣告，但具有相同名稱的屬性化結構已存在。 向前宣告的屬性會被忽略。

下列範例會產生 C4926：

```
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```