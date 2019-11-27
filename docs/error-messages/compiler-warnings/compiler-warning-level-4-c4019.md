---
title: 編譯器警告 (層級 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: b15d024f217280fb4fc49242f4bfc1e7fcc2b303
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541230"
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