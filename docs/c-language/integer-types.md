---
title: 整數類型
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 23da055b56e2ae77fed796d9ba8e7f227e572a9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232848"
---
# <a name="integer-types"></a>整數類型

每個整數常數都會根據其值和表示方式而被指定特定類型。 您可以將所有整數常數的類型強制指定為 **long**，方法是在常數結尾加上字母 **l** 或 **L**；也可以將其類型強制指定為 `unsigned`，方法是在其值後面加上 **u** 或 **U**。 小寫字母 **l** 與數字 1 容易混淆，應予以避免。 部分 **long** 形式的整數常數如下：

```
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

您指派給常數的類型取決於該常數所代表的值。 常數的值必須介於其類型可以代表的值的範圍內。 常數的類型決定在運算式中使用常數時，或套用負號（**-**）時，所要執行的轉換。 這份清單摘要說明整數常數的轉換規則。

- 沒有尾碼的十進位常數類型為`int`、 **long int**或不帶正負號的**long int**。這三種類型中的第一個，可以用來表示常數的值是指派給常數的類型。

- 視常數的大小而定，指派給八進位和十六進位常數 (沒有尾碼) 的類型是 `int`、`unsigned int`、**long int** 或 **unsigned long int**。

- 視常數的大小而定，指派給尾碼為 **u** 或 **U** 之常數的類型是 **unsigned int** 或 **unsigned long int**。

- 視常數的大小而定，指派給尾碼為 **l** 或 **L** 之常數的類型是 **long int** 或 **unsigned long int**。

- 指派給尾碼為 **u** 或 **U** 及 **l** 或 **L** 之常數的類型是 **unsigned long int**。

## <a name="see-also"></a>請參閱

[C 整數常數](../c-language/c-integer-constants.md)
