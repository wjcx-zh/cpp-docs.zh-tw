---
title: 基本類型 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c24ee360f1c14aa9b355f45ec1c12877efa306c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="fundamental-types--c"></a>基本類型 (C++)
C++ 中的基本類型分為三類：整數、浮點和 void。 整數類資料類型能夠處理整數。 浮點類型可以指定可能有小數部分的值。  
  
 [void](../cpp/void-cpp.md) 類型描述一組空值。 不可以指定 `void` 類型的變數 -- 該類型主要是用來宣告沒有傳回值的函式，或是將泛型指標宣告為不具類型或任意具類型的資料。 所有運算式都可以明確轉換或轉型為類型 `void`。 不過，這類運算式僅限於下列用法：  
  
-   運算陳述式 (如需詳細資訊，請參閱 [運算式](../cpp/expressions-cpp.md))。  
  
-   逗號運算子的左運算元 (如需詳細資訊，請參閱 [逗號運算子](../cpp/comma-operator.md) )。  
  
-   條件運算子的第二個或第三個運算元 (`? :`)。 (如需詳細資訊，請參閱 [含條件運算子的運算式](../cpp/conditional-operator-q.md) )。  
  
 下表說明類型大小的限制。 這些限制與 Microsoft 實作無關。  
  
### <a name="fundamental-types-of-the-c-language"></a>C++ 語言的基本類型  
  
|分類|類型|內容|  
|--------------|----------|--------------|  
|整數|`char`|`char` 類型是通常包含基本執行字元集成員的整數類資料類型；根據預設，這是 Microsoft C++ 中的 ASCII。<br /><br /> C++ 編譯器會將類型為 `char`, `signed` `char`和 `unsigned` `char` 的變數視為具有不同的類型。 除非使用 /J 編譯選項，否則會將 `char` 類型的變數提升為 `int` ，就如同這些變數已預設為 `signed` `char` 類型一樣。 在這種情況下，會將這些變數視為 `unsigned` `char` 類型，並提升為不帶正負號的 `int` 。|  
||`bool`|`bool` 類型是可以具有 `true` 或 `false`兩個值之一的整數類資料類型。 它的大小並未指定。|  
||`short`|`short` `int` (或只是 `short`) 類型是大於或等於 `char`類型大小，但短於或等於 `int`類型大小的整數類資料類型。<br /><br /> `short` 類型的物件可以宣告為 `signed` `short` 或 `unsigned short`。 `Signed short` 與 `short`同義。|  
||`int`|`int` 類型是大於或等於 `short` `int`類型大小，但短於或等於 `long`類型大小的整數類資料類型。<br /><br /> `int` 類型的物件可以宣告為 `signed` `int` 或 `unsigned` `int`。 `Signed` `int` 與 `int`同義。|  
||`__int8`、 `__int16`、 `__int32`、 `__int64`|可調整大小的整數 `__int n`，其中 `n` 是整數變數的大小 (以位元為單位)。 `__int8`、 `__int16`、 `__int32` 和 `__int64` 是 Microsoft 特定的關鍵字。 並非所有類型都都適用於所有架構。 `(__int128` 不支援。）|  
||`long`|`long` (或 `long` `int`) 類型是大於或等於 `int`類型大小的整數類資料類型。<br /><br /> `long` 類型的物件可以宣告為 `signed` `long` 或 `unsigned` `long`。 `Signed` `long` 與 `long`同義。|  
||`long` `long`|大於不帶正負號的 `long`。<br /><br /> `long long` 類型的物件可以宣告為 `signed` `long long` 或 `unsigned` `long long`。 `signed` `long long` 是的同義字`long long`。|  
||`wchar_t`, `__wchar_t`|`wchar_t` 類型的變數指定寬字元或多位元組字元類型。 根據預設， `wchar_t` 是原生類型，但是您可以使用 [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ，將 `wchar_t` 設為 `unsigned short`的 typedef。 `__wchar_t` 是 Microsoft 特定的類型，與原生 `wchar_t` 類型同義。<br /><br /> 在字元或字串常數之前使用 L 前置詞，指定寬字元類型。|  
|浮點|`float`|`float` 類型是最小的浮點類型。|  
||`double`|`double` 類型是大於或等於 `float`類型，但短於或等於 `long` `double`類型大小的浮點類型。<br /><br /> Microsoft 特定的： `long double` 和 `double` 的表示法相同。 不過， `long double` 和 `double` 是不同的類型。|  
||`long double`|`long` `double` 類型是大於或等於 `double`類型的浮點類型。|  
  
 **Microsoft 特定的**  
  
 下表列出 Microsoft C++ 的基本類型所需的儲存空間量。  
  
### <a name="sizes-of-fundamental-types"></a>基本類型的大小  
  
|類型|大小|  
|----------|----------|  
|`bool`、 `char`、 `unsigned char`、 `signed char`、 `__int8`|1 個位元組|  
|`__int16`、 `short`、 `unsigned short`、 `wchar_t`、 `__wchar_t`|2 個位元組|  
|`float`、 `__int32`、 `int`、 `unsigned int`、 `long`、 `unsigned long`|4 個位元組|  
|`double`、 `__int64`、 `long double`、 `long long`|8 個位元組|  
  
 **結束 Microsoft 特定的**  
  
 如需每個類型值範圍的摘要，請參閱 [資料類型範圍](../cpp/data-type-ranges.md) 。  
  
 如需類型轉換的詳細資訊，請參閱 [標準轉換](../cpp/standard-conversions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型範圍](../cpp/data-type-ranges.md)