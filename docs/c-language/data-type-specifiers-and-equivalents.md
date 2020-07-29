---
title: 資料類型規範和對應項
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
ms.openlocfilehash: bfbca4ae87d84286b94120eaf24de928ae75f3c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200318"
---
# <a name="data-type-specifiers-and-equivalents"></a>資料類型規範和對應項

本書通常會使用下表所列之類型規範的形式，而不是完整格式，並假設該 **`char`** 類型預設為已簽署。 因此，在本書中， **`char`** 相當於 **`signed char`** 。

## <a name="type-specifiers-and-equivalents"></a>類型規範及對等項目

|類型規範|對等項目|
|--------------------|---------------------|
|**`signed char`** sha-1|**`char`**|
|**`signed int`**|**`signed`**, **`int`**|
|**`signed short int`**|**`short`**, **`signed short`**|
|**`signed long int`**|**`long`**, **`signed long`**|
|**`unsigned char`**|—|
|**`unsigned int`**|**`unsigned`**|
|**`unsigned short int`**|**`unsigned short`**|
|**`unsigned long int`**|**`unsigned long`**|
|**`float`**|—|
|**`long double`** 2|—|

1當您 **`char`** 依預設讓類型不帶正負號（藉由指定 **`/J`** 編譯器選項）時，您不能將縮寫 **`signed char`** 為 **`char`** 。

2在32位和64位作業系統中，Microsoft C 編譯器會對應 **`long double`** 至類型 **`double`** 。

**Microsoft 特定的**

您可以指定 **`/J`** 編譯器選項，將預設 **`char`** 類型從變更 **`signed char`** 為 **`unsigned char`** 。 當這個選項生效時， **`char`** 表示與相同 **`unsigned char`** ，而且您必須使用 **`signed`** 關鍵字來宣告帶正負號的字元值。 如果明確宣告了某個 **`char`** 值 **`signed`** ，則 **`/J`** 選項不會影響它，而且當擴展為類型時，此值會進行正負號擴充 **`int`** 。 **`char`** 當擴展成類型時，類型會以零擴充 **`int`** 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C 類型規範](../c-language/c-type-specifiers.md)
