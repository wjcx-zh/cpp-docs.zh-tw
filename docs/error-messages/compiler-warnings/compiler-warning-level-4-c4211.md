---
title: 編譯器警告 (層級 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6387f58430098e49e7add25e8915bf6b181634e9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541835"
---
# <a name="compiler-warning-level-4-c4211"></a>編譯器警告 (層級 4) C4211

使用非標準的擴充：已將 extern 重新定義為靜態

使用預設的 Microsoft 擴充功能（/Ze）時，您可以將 `extern` 識別碼重新定義為**靜態**。

## <a name="example"></a>範例

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，這類重新定義無效。
