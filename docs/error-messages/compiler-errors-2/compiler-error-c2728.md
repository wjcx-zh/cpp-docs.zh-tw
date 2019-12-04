---
title: 編譯器錯誤 C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: ac9efa88fc4ab17a656172c44de2e49e82108108
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755664"
---
# <a name="compiler-error-c2728"></a>編譯器錯誤 C2728

'type'：原生陣列不可包含這個類型

陣列建立語法是用來建立 Managed 或 WinRT 物件的陣列。 您不能使用原生陣列語法建立 Managed 或 WinRT 物件的陣列。

如需詳細資訊，請參閱 [陣列](../../extensions/arrays-cpp-component-extensions.md)。

下列範例會產生 C2728，並示範如何修正此問題：

```cpp
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
