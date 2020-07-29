---
title: 編譯器錯誤 C2046
ms.date: 11/04/2016
f1_keywords:
- C2046
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
ms.openlocfilehash: b95aa6fd7ef8a1ce2a5fc45e47cfea20e4c38f8c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210913"
---
# <a name="compiler-error-c2046"></a>編譯器錯誤 C2046

case 的使用不合法

關鍵字只能 `case` 出現在 **`switch`** 語句中。

下列範例會產生 C2046：

```cpp
// C2046.cpp
int main() {
   case 0:   // C2046
}
```

可能的解決方式：

```cpp
// C2046b.cpp
int main() {
   int i = 0;

   switch(i) {
      case 0:
      break;

      default:
      break;
   }
}
```
