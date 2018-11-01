---
title: 編譯器警告 (層級 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: d2bfec799b8b2981914b76839e51b7a0d09b30ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465373"
---
# <a name="compiler-warning-level-4-c4019"></a>編譯器警告 (層級 4) C4019

在全域範圍有空的陳述式

全域範圍的分號前面沒有陳述式。

如果您移除多餘的分號，可能即會修正這個警告。

## <a name="example"></a>範例

```
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```