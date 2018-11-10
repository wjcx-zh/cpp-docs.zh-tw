---
title: 初始化純量類型
ms.date: 11/04/2016
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
ms.openlocfilehash: f991eff82e5b6919f7960513ae9bc502cad77069
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641086"
---
# <a name="initializing-scalar-types"></a>初始化純量類型

初始化純量類型時，會將 *assignment-expression* 的值指派給變數。 指派適用的轉換規則。 (如需轉換規則的詳細資訊，請參閱[類型轉換](../c-language/type-conversions-c.md))。

## <a name="syntax"></a>語法

*宣告*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告子* **=** *初始設定式* /\* 針對純量初始設定式 \*/

*initializer*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*

您可以在遵守下列規則的情況下初始化任何類型的變數：

- 可以初始化在檔案範圍層級宣告的變數。 如果您未在外部層級明確初始化變數，該變數預設會初始化為 0。

- 常數運算式可以用來初始化所有使用 **static** *storage-class-specifier* 宣告的全域變數。 在程式執行開始時，會初始化宣告為 **static** 的變數。 如果您未明確初始化全域 **static** 變數，預設會將該變數初始化為 0，因此會為所有具有指標類型的成員指派 null 指標。

- 使用 **auto** 或 **register** 儲存類別指定名稱宣告的變數，會在每次執行控制項傳遞到宣告這些變數的區塊時進行初始化。 如果在宣告時省略 **auto** 或 **register** 變數的初始設定式，則變數的初始值會是未定義狀態。 若為自動和暫存器值，初始設定式不限於是常數，它可以是包含先前定義之值 (即使是函數呼叫) 的運算式。

- 外部變數宣告和所有 **static** 變數 (外部或內部) 的初始值都必須是常數運算式。 (如需詳細資訊，請參閱[常數運算式](../c-language/c-constant-expressions.md))。由於任何外部宣告或靜態變數的位址都是常數，因此可以用來初始化內部宣告的 **static** 指標變數。 不過，由於每次在執行區塊時，**auto** 變數的位址可能會有所不同，因此無法使用該位址做為靜態初始設定式。 您可以使用常數或變數值初始化 **auto** 和 **register** 變數。

- 如果識別項的宣告具有區塊範圍，而且識別項具有外部連結，則此宣告不能有初始化。

## <a name="examples"></a>範例

下列範例將說明初始化：

```C
int x = 10;
```

整數變數 `x` 已初始化為常數運算式 `10`。

```C
register int *px = 0;
```

指標 `px` 已初始化為 0，產生了一個 "null" 指標。

```C
const int c = (3 * 1024);
```

這個範例使用常數運算式 `(3 * 1024)` 將 `c` 初始化為一個無法修改的常數值，因為使用了 **const** 關鍵字。

```C
int *b = &x;
```

這個陳述式初始化具有另一個變數 `b` 之位址的指標 `x`。

```C
int *const a = &z;
```

使用名為 `a` 的變數位址初始化指標 `z`。 不過，因為其指定為 **const`a`，因此變數**  只能進行初始化，而無法進行修改。 其永遠指向相同的位置。

```C
int GLOBAL ;

int function( void )
{
    int LOCAL ;
    static int *lp = &LOCAL;   /* Illegal initialization */
    static int *gp = &GLOBAL;  /* Legal initialization   */
    register int *rp = &LOCAL; /* Legal initialization   */
}
```

全域變數 `GLOBAL` 是在外部層次宣告，因此具有全域存留期。 區域變數 `LOCAL` 具有 **auto** 儲存類別，且在宣告該變數的函式執行期間只具有位址。 因此，不允許使用 `lp` 的位址初始化 **static** 指標變數 `LOCAL`。 因為該位址永遠相同，所以 **static** 指標變數 `gp` 可以初始化至 `GLOBAL` 的位址。 同樣地，您可以初始化 `*rp`，因為 `rp` 是區域變數，並可能具有非常數的初始設定式。 每當進入區塊時，`LOCAL` 會擁有新的位址，接著再將其指派給 `rp`。

## <a name="see-also"></a>請參閱

[初始化](../c-language/initialization.md)