---
title: 編譯器錯誤 C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: 7366995f8930b4733ccff73aef38ebcf65a0c120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575652"
---
# <a name="compiler-error-c2054"></a>編譯器錯誤 C2054

必須是 ' (' 遵循 'identifier'

需要後端的括號內容中使用函式識別項。

此錯誤可能被因省略複雜初始化等號 （=）。

下列範例會產生 C2054:

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

可能的解決方式：

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```