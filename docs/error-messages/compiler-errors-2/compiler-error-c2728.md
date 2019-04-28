---
title: 編譯器錯誤 C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 1fbbc3d63386ebe98a447de8b7166a5263d2168f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208411"
---
# <a name="compiler-error-c2728"></a>編譯器錯誤 C2728

'type'：原生陣列不可包含這個類型

陣列建立語法是用來建立 Managed 或 WinRT 物件的陣列。 您不能使用原生陣列語法建立 Managed 或 WinRT 物件的陣列。

如需詳細資訊，請參閱 [陣列](../../extensions/arrays-cpp-component-extensions.md)。

下列範例會產生 C2728，並示範如何修正此問題：

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
