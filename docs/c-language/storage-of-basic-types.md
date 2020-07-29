---
title: 基本類型的儲存
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: 973866a912b694510d587df765ac8dd54176638e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211667"
---
# <a name="storage-of-basic-types"></a>基本類型的儲存

下表摘要說明與每個基本類型相關聯的儲存區。

## <a name="sizes-of-fundamental-types"></a>基本類型的大小

|類型|儲存體|
|----------|-------------|
|**`char`**, **`unsigned char`**, **`signed char`**|1 個位元組|
|**`short`**, **`unsigned short`**|2 個位元組|
|**`int`**, **`unsigned int`**|4 個位元組|
|**`long`**, **`unsigned long`**|4 個位元組|
|**`long long`**, **`unsigned long long`**|8 個位元組|
|**`float`**|4 個位元組|
|**`double`**|8 個位元組|
|**`long double`**|8 個位元組|

C 資料類型屬於一般分類。 *整數類資料類型*包括 **`int`** 、 **`char`** 、 **`short`** 、 **`long`** 和 **`long long`** 。 這些型別可以使用或來限定 **`signed`** **`unsigned`** ，而且 **`unsigned`** 本身可用來做為的速記 **`unsigned int`** 。 列舉型別（ **`enum`** ）在大部分的用途中也視為整數型別。 *浮動類型*包括 **`float`** 、 **`double`** 和 **`long double`** 。 *算術類型*包含所有浮點和整數類型。

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
