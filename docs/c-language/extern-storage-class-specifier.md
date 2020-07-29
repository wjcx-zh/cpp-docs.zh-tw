---
title: extern 儲存類別指定名稱
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: e3242f86e30dcf3227586400b83266ad366ec7e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217099"
---
# <a name="extern-storage-class-specifier"></a>extern 儲存類別指定名稱

以儲存類別指定名稱宣告的變數 **`extern`** ，就是在另一個原始檔中定義了同名變數的參考。 它可用來公開外部層級的變數定義。 宣告為的變數 **`extern`** 沒有配置給本身的儲存體，它只是名稱。

## <a name="example"></a>範例

下列範例說明內部和外部層級宣告：

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

在此範例中，變數 `i` 定義在 Source1.c 中且初始值為 1。 **`extern`** Source2 中的宣告會使 ' i ' 顯示在該檔案中。

在函式中 `func` ，全域變數的位址 `i` 是用來初始化 **`static`** 指標變數 `external_i` 。 這是因為全域變數具有 **`static`** 存留期，這表示其位址不會在程式執行期間變更。 接下來，變數 `i` 是定義在 `func` 範圍內的區域變數，且初始值為 16。 這個定義不會影響外部層級 `i` 的值，將其名稱用於區域變數會將之隱藏。 全域 `i` 的值現在只能透過指標 `external_i` 來存取。

## <a name="see-also"></a>另請參閱

[內部層級宣告的儲存類別指定名稱](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
