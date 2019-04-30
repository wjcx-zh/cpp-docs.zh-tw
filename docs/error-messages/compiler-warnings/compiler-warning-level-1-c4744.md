---
title: 編譯器警告 (層級 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 2118a32af8b99d35c1e1a6691561391ec5d2b8cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385416"
---
# <a name="compiler-warning-level-1-c4744"></a>編譯器警告 (層級 1) C4744

'var' 具有 'file1' 和 'file2' 中的不同類型: 'type1' 和 'type2'

在兩個檔案中定義或參考的外部變數會有不同類型，這些檔案中。  若要解決，讓型別定義相同，或是變更其中一個檔案中的變數名稱。

檔案以 /gl 編譯時，才會發出 C4744  如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
>  C4744 通常會發生在 C 中 (沒有C++) 檔案，因為在C++變數的名稱裝飾型別資訊。  範例 （如下所示） 時做為編譯C++，您會收到連結器錯誤 LNK2019。

## <a name="example"></a>範例

此範例包含的第一個定義。

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>範例

下列範例會產生 C4744。

```
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