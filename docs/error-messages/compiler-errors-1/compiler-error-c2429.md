---
title: 編譯器錯誤 C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: 972ec6591132443ef4d1297598d6de7216f59663
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586689"
---
# <a name="compiler-error-c2429"></a>編譯器錯誤 C2429

> '*語言功能*'需要編譯器旗標'*編譯器選項*'

語言功能需要支援特定的編譯器選項。

錯誤**C2429： 語言功能 '巢狀命名空間-定義' 需要編譯器旗標 ' / /std: c + + 17'** 如果您嘗試定義就會產生*複合的命名空間*，包含一或多個命名空間從 Visual Studio 2015 Update 5 的範圍巢狀命名空間名稱。 (在 Visual Studio 2017 15.3 版中， **/std: c + + 最新**參數是必要。)複合定義 c + + 中不允許在 c++17 之前的命名空間。 編譯器支援複合的命名空間定義時[/std: c + + 17](../../build/reference/std-specify-language-standard-version.md)編譯器選項指定：

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
