---
title: 編譯器警告 (層級 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367384"
---
# <a name="compiler-warning-level-1-c4744"></a>編譯器警告 (層級 1) C4744

"var"在"file1"和"file2"中有不同的類型:"類型 1"和"類型 2"

在兩個檔中引用或定義的外部變數在這些檔中具有不同的類型。  要解決,請使類型定義相同,或更改其中一個檔中的變數名稱。

僅當使用 /GL 編譯檔時,才會發出 C4744。  如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
> C4744 通常發生在 C(不是C++)檔中,因為在C++變數名稱用類型資訊修飾。  當範例(下圖)編譯為C++時,您將獲得連結器錯誤 LNK2019。

## <a name="example"></a>範例

此示例包含第一個定義。

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>範例

以下示例生成C4744。

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
