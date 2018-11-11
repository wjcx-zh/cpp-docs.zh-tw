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
ms.openlocfilehash: 426bf816b988730530ba52c3f995aa2b0a8f0140
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650311"
---
# <a name="extern-storage-class-specifier"></a>extern 儲存類別指定名稱

使用 **extern** 儲存類別指定名詞宣告的變數，會參考其他來源檔案中使用相同名稱定義的變數。 它可用來公開外部層級的變數定義。 宣告為 **extern** 的變數並沒有自己的配置儲存體，而只是一個名稱。

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

在此範例中，變數 `i` 定義在 Source1.c 中且初始值為 1。 在 Source2.c 中的 **extern** 宣告使 'i' 公開於該檔案中。

在 `func` 函式中，全域變數 `i` 的位址會用來初始化 **static** 指標變數 `external_i`。 因為全域變數具有 **static** 存留期，也就是說它的位址不會在程式執行期間變更，所以才能這樣運作。 接下來，變數 `i` 是定義在 `func` 範圍內的區域變數，且初始值為 16。 這個定義不會影響外部層級 `i` 的值，將其名稱用於區域變數會將之隱藏。 全域 `i` 的值現在只能透過指標 `external_i` 來存取。

## <a name="see-also"></a>請參閱

[內部層級宣告的儲存類別規範](../c-language/storage-class-specifiers-for-internal-level-declarations.md)