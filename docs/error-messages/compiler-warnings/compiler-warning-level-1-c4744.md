---
title: 編譯器警告 (層級 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 9f63da4acd87ef2bb0ba80df9e8c0e3e3db4bc79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185642"
---
# <a name="compiler-warning-level-1-c4744"></a>編譯器警告 (層級 1) C4744

' file1 ' 和 ' file2 ' 中的 ' var ' 類型不同： ' type1 ' 和 ' type2 '

在兩個檔案中參考或定義的外部變數在這些檔案中具有不同的類型。  若要解決此問題，請將類型定義設為相同，或變更其中一個檔案中的變數名稱。

只有在使用/GL. 編譯檔案時，才會發出 C4744  如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
>  C4744 通常會發生在 C （ C++非）檔案中， C++因為在變數名稱中，會以類型資訊裝飾。  當範例（下方）編譯為C++時，您會收到連結器錯誤 LNK2019。

## <a name="example"></a>範例

這個範例包含第一個定義。

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>範例

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
