---
title: 編譯器警告 (層級 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 31711d3709b7c2ae3658d760f538ea9e841d33a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655720"
---
# <a name="compiler-warning-level-4-c4214"></a>編譯器警告 (層級 4) C4214

使用非標準擴充： 位元非整數的欄位類型

使用預設的 Microsoft 擴充功能 (/Ze) 中，位元欄位的結構成員可以是任何整數類型。

## <a name="example"></a>範例

```
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

這類的位元欄位是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。