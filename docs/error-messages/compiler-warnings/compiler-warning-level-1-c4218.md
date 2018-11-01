---
title: 編譯器警告 (層級 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 36d5de3b1270b41edfc391df960a556aca207709
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555294"
---
# <a name="compiler-warning-level-1-c4218"></a>編譯器警告 (層級 1) C4218

使用非標準擴充： 必須指定至少一個儲存體類別或類型

使用預設的 Microsoft 擴充功能 (/Ze) 中，您可以宣告變數，而不需要指定類型或存放裝置類別。 預設類型為 `int`。

## <a name="example"></a>範例

```
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

這類宣告是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。