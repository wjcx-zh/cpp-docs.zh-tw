---
title: 編譯器警告 （層級 1） C4218 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1970dd1bd231716f59508a7cca9f82d3e13151ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074041"
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