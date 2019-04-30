---
title: 編譯器警告 (層級 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 44f49705bf197d7a42b80e50983e47a4c0ce7bed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401198"
---
# <a name="compiler-warning-level-4-c4207"></a>編譯器警告 (層級 4) C4207

使用非標準擴充： 擴充形式的初始設定式

使用 Microsoft 擴充功能 (/Ze)，您可以初始化可變大小的陣列的`char`使用大括號內的字串。

## <a name="example"></a>範例

```
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。