---
title: 編譯器警告 (層級 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 38a05c04181efb95ec3e7549c40056b8d223e128
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685550"
---
# <a name="compiler-warning-level-1-c4744"></a>編譯器警告 (層級 1) C4744

' file1 ' 和 ' file2 ' 中的 ' var ' 具有不同的類型： ' type1 ' 和 ' type2 '

在兩個檔案中參考或定義的外部變數在這些檔案中有不同的類型。  若要解決此問題，請讓類型定義相同，或變更其中一個檔案中的變數名稱。

只有當檔案以/GL 編譯時，才會發出 C4744  如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
> C4744 通常會發生在 C (非 c + +) 檔中，因為在 c + + 中，變數名稱會以類型資訊裝飾。  當下列) 的範例 (編譯為 c + + 時，您將會收到連結器錯誤 LNK2019。

## <a name="examples"></a>範例

此範例包含第一個定義。

```c
// C4744.c
// compile with: /c /GL
int global;
```

下列範例會產生 C4744。

```c
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```
