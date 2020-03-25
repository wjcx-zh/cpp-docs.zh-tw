---
title: 編譯器警告 (層級 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 70dadb7d424352fbde8c5904053b22fe7cc6b77e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161278"
---
# <a name="compiler-warning-level-4-c4214"></a>編譯器警告 (層級 4) C4214

使用非標準的擴充：不是 int 的位欄位類型

使用預設的 Microsoft 擴充功能（/Ze）時，位結構成員可以是任何整數類型。

## <a name="example"></a>範例

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，這類位欄位是不正確。
