---
title: 整數類型
ms.date: 07/22/2020
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 61ed64c613bc88ed5bf62999ba77fa4090c1ec4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211797"
---
# <a name="integer-types"></a>整數類型

每個整數常數都會根據其值和其表示方式來指定類型。 您可以藉 **`long`** 由附加字母或常數結尾來強制輸入任何整數常數 **`l`** **`L`** ; 您可以藉 **`unsigned`** 由將 **`u`** 或附加至值，強制將其設為類型 **`U`** 。 小寫字母 **`l`** 可以與數位1混淆，應予以避免。 某些形式的 **`long`** 整數常數如下所示：

```C
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

您指派給常數的類型取決於該常數所代表的值。 常數的值必須介於其類型可以代表的值的範圍內。 常數的類型決定在運算式中使用常數時，或套用負號（）時，所要執行的轉換 **`-`** 。 這份清單摘要說明整數常數的轉換規則。

- 沒有尾碼的十進位常數類型為 **`int`** 、 **`long int`** 或 **`unsigned long int`** 。 在可以表示常數值的這三種類型中，會將第一種指派給常數。

- 指派給八進位和十六進位常數（沒有尾碼）的類型是 **`int`** 、 **`unsigned int`** 、 **`long int`** 或， **`unsigned long int`** 視常數的大小而定。

- 指派給具有 **`u`** 或尾碼之常數的類型 **`U`** 是 **`unsigned int`** 或（ **`unsigned long int`** 視其大小而定）。

- 指派給具有 **`l`** 或尾碼之常數的類型 **`L`** 是 **`long int`** 或（ **`unsigned long int`** 視其大小而定）。

- 指派給具有或之常數的 **`u`** 類型 **`U`** ， **`l`** 或 **`L`** 尾碼為 **`unsigned long int`** 。

## <a name="see-also"></a>另請參閱

[C 整數常數](../c-language/c-integer-constants.md)
