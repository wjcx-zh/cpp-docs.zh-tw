---
title: 編譯器警告 (層級 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 1ff669512f85dfed9bab307c2986e7858285461d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161382"
---
# <a name="compiler-warning-level-4-c4207"></a>編譯器警告 (層級 4) C4207

使用非標準的擴充：擴充初始化運算式表單

使用 Microsoft extensions （/Ze）時，您可以使用括弧括住的字串，初始化 `char` 的可變大小陣列。

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
