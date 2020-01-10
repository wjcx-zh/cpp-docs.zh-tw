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
ms.openlocfilehash: 64c642df4dd85e4aa09f90a143b8aa67c28b7dc2
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998770"
---
# <a name="storage-of-basic-types"></a>基本類型的儲存

下表摘要說明與每個基本類型相關聯的儲存區。

## <a name="sizes-of-fundamental-types"></a>基本類型的大小

|Type|儲存體|
|----------|-------------|
|**char**、不**帶正負**號的 char、**帶正負**號的字元|1 個位元組|
|**short**、**unsigned short**|2 個位元組|
|**int**、**unsigned int**|4 個位元組|
|**long**、**unsigned long**|4 個位元組|
|**長**長、不**帶正負**號的長長|8 個位元組|
|**float**|4 個位元組|
|**double**|8 個位元組|
|**long double**|8 個位元組|

C 資料類型屬於一般分類。 *整數類資料類型*包括**int**、 **char**、 **short**、 **long**和**long long**。 這些型別可以使用**帶正負**號**或不帶正負**號的格式來限定，而且不帶**正負**號的會當做不**帶正負號 int**的速記列舉型別（**enum**）在大部分的用途中也會被視為整數型別。 *浮點類型*包括**float**、 **double**和**long double**。 *算術類型*包含所有浮點和整數類型。

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
