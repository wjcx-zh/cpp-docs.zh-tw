---
title: 編譯器警告 (層級 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: 6245a32aff0769a2f30dfe88ca6111579eda6ea9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185460"
---
# <a name="compiler-warning-level-4-c4019"></a>編譯器警告 (層級 4) C4019

在全域範圍有空的陳述式

全域範圍的分號前面沒有陳述式。

如果您移除多餘的分號，可能即會修正這個警告。

## <a name="example"></a>範例

```c
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```
