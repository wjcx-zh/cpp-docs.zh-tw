---
title: C 位元欄位
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
ms.openlocfilehash: 4878a9c8c206851b13484446b436952e655e06db
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234285"
---
# <a name="c-bit-fields"></a>C 位元欄位

除了結構或等位成員的宣告子之外，結構宣告子也可以指定為位元數目 (稱為「位元欄位」)。 其長度是依冒號從欄位名稱的宣告子所設定。 位元欄位會以整數類型解譯。

## <a name="syntax"></a>語法

*結構聲明*子宣告子：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型規範* *declarator*宣告子<sub>opt</sub> **：** *常數運算式*

*constant-expression* 會以位元指定欄位的寬度。 的*類型規範* `declarator` 必須是 **`unsigned int`** 、 **`signed int`** 或 **`int`** ，而且*常數運算式*必須是非負整數值。 若該值是零，宣告沒有 `declarator`。 不允許位元欄位陣列、位元欄位指標與傳回位元欄位的函式。 選擇性的 `declarator` 會為位元欄位命名。 位元欄位只能宣告為結構的一部分。 不能將通訊運算子（ **&** ）套用至位欄位元件。

無法參考未具名位元欄位，而且其內容在執行階段無法預測。 它們可以當作「虛設」欄位使用，以用於對齊用途。 將寬度指定為0的未命名位欄位，可保證在*結構宣告清單*中後面的成員儲存體會從 **`int`** 界限開始。

位元欄位也必須夠長，以包含位元模式。 例如，這兩個陳述式不合法：

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

此範例定義名為 `screen` 之結構的二維陣列。

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

陣列包含 2,000 個元素。 每個元素都是個別的結構，其中包含四個位元欄位成員：`icon`、`color`、`underline` 與 `blink`。 每個結構的大小都是兩位元組。

位元欄位具有與整數類型相同的語意。 此表示位元欄位在運算式的使用方式，就像使用相同基底類型的變化一樣，而不論位元欄位中有多少位元。

**Microsoft 特定的**

定義為的位欄位 **`int`** 會視為 **`signed`** 。 ANSI C 標準的 Microsoft 擴充功能允許 **`char`** **`long`** **`signed`** 位欄位的和類型（和 **`unsigned`** ）。 具有基底類型 **`long`** 、或（或）的未命名位欄位，會 **`short`** **`char`** **`signed`** **`unsigned`** 強制對齊適合基底類型的界限。

位元欄位是在整數內依最小顯著性到最高有效位元的順序配置。 在下列程式碼中

```
struct mybitfields
{
    unsigned short a : 4;
    unsigned short b : 5;
    unsigned short c : 7;
} test;

int main( void );
{
    test.a = 2;
    test.b = 31;
    test.c = 0;
}
```

位元排列如下：

```
00000001 11110010
cccccccb bbbbaaaa
```

因為 8086 系列處理器會先儲存整數值的低位元組，再儲存高位元組，上面的整數 `0x01F2` 將儲存到實體記憶體作為 `0xF2`，後面接著 `0x01`。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[結構宣告](../c-language/structure-declarations.md)
