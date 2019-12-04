---
title: 編譯器錯誤 C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 7166ba4e5f3a0fb66360d388fb18367bf553492e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750451"
---
# <a name="compiler-error-c2117"></a>編譯器錯誤 C2117

' identifier '：陣列界限溢位

陣列具有太多初始化運算式：

- 陣列元素和初始化運算式不符合大小和數量。

- 字串中的 null 結束字元沒有空格。

下列範例會產生 C2117：

```cpp
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```
