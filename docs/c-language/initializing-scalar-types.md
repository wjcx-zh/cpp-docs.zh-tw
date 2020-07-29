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
ms.openlocfilehash: 063761abcbb1541893b9cbab463e3d121684d00a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211823"
---
# <a name="initializing-scalar-types"></a>初始化純量類型

初始化純量類型時，的值 *`assignment-expression`* 會指派給變數。 指派適用的轉換規則。 (如需轉換規則的詳細資訊，請參閱[類型轉換](../c-language/type-conversions-c.md))。

## <a name="syntax"></a>語法

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`init-declarator-list`* <sub>opt</sub>**`;`**

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`storage-class-specifier`**`declaration-specifiers`* <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-specifier`**`declaration-specifiers`* <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-qualifier`**`declaration-specifiers`* <sub>opt</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`***`=`** *`initializer`* /\*針對純量初始化\*/

*`initializer`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assignment-expression`*

您可以在遵守下列規則的情況下初始化任何類型的變數：

- 可以初始化在檔案範圍層級宣告的變數。 如果您未在外部層級明確初始化變數，該變數預設會初始化為 0。

- 常數運算式可以用來初始化使用所宣告的任何全域變數 **`static`** *`storage-class-specifier`* 。 **`static`** 當程式開始執行時，會初始化宣告為的變數。 如果您未明確初始化全域 **`static`** 變數，則預設會將它初始化為0，而且具有指標類型的每個成員都會被指派 null 指標。

- 使用或儲存類別指定名稱宣告的變數 **`auto`** **`register`** 會在每次執行控制傳遞至其宣告所在的區塊時進行初始化。 如果您省略或變數宣告中的初始化運算式 **`auto`** **`register`** ，則變數的初始值會是未定義的。 若為自動和暫存器值，初始設定式不限於是常數，它可以是包含先前定義之值 (即使是函數呼叫) 的運算式。

- 外部變數宣告和所有 **`static`** 變數（不論是外部或內部）的初始值都必須是常數運算式。 （如需詳細資訊，請參閱[常數運算式](../c-language/c-constant-expressions.md)）。由於任何外部宣告或靜態變數的位址都是常數，因此可以用來初始化內部宣告的 **`static`** 指標變數。 不過，變數的位址 **`auto`** 無法當做靜態初始化運算式使用，因為每次執行區塊時，它可能會不同。 您可以使用常數或變數值來初始化 **`auto`** 和 **`register`** 變數。

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

這個範例使用常數運算式 `(3 * 1024)` 來初始化 `c` 為常數值，因為關鍵字是無法修改的 **`const`** 。

```C
int *b = &x;
```

這個陳述式初始化具有另一個變數 `b` 之位址的指標 `x`。

```C
int *const a = &z;
```

使用名為 `a` 的變數位址初始化指標 `z`。 不過，因為它指定為 **`const`** ，所以 `a` 只能初始化變數，而永不修改。 其永遠指向相同的位置。

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

全域變數 `GLOBAL` 是在外部層次宣告，因此具有全域存留期。 本機變數 `LOCAL` 具有 **`auto`** 儲存類別，而且在其宣告所在的函式執行期間只會有位址。 因此， **`static`** `lp` 不允許嘗試使用位址初始化指標變數 `LOCAL` 。 **`static`** 指標變數 `gp` 可以初始化為的位址， `GLOBAL` 因為該位址一律相同。 同樣地， `*rp` 可以初始化，因為 `rp` 是本機變數，而且可以有非常數初始化運算式。 每當進入區塊時，`LOCAL` 會擁有新的位址，接著再將其指派給 `rp`。

## <a name="see-also"></a>另請參閱

[初始](../c-language/initialization.md)
