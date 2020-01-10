---
title: 編譯器錯誤 C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 54fa7de8eb3df8d4b3695544c5285cc202275492
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745911"
---
# <a name="compiler-error-c3153"></a>編譯器錯誤 C3153

' interface '：您無法建立介面的實例

無法具現化介面。 若要使用介面的成員，請從介面衍生類別、執行介面成員，然後使用成員。

下列範例會產生 C3153：

```cpp
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
