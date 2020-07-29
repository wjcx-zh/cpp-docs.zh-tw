---
title: 編譯器警告 (層級 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: e694f96d7f6271686d1b2a19e5a12e5e08e1cfbe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219946"
---
# <a name="compiler-warning-level-4-c4207"></a>編譯器警告 (層級 4) C4207

使用非標準的擴充：擴充初始化運算式表單

使用 Microsoft extensions （/Ze）時，您可以使用括弧括住的字串，初始化的可變大小陣列 **`char`** 。

## <a name="example"></a>範例

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

這類初始化在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下無效。
