---
title: 基本類型 (C++)
ms.date: 11/04/2016
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
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: daa2ad2680a9d7d0239a70ed37ec1d90a3d96d97
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857537"
---
# <a name="fundamental-types--c"></a>基本類型 (C++)

C++ 中的基本類型分為三類：整數、浮點和 void。 整數類資料類型能夠處理整數。 浮點類型可以指定可能有小數部分的值。

[void](../cpp/void-cpp.md) 類型描述一組空值。 無法指定**void**類型的變數，其主要用於宣告不傳回任何值的函式，或宣告不具類型或任意類型資料的泛型指標。 任何運算式都可以明確轉換或轉換成**void**類型。 不過，這類運算式僅限於下列用法：

- 運算陳述式 (如需詳細資訊，請參閱 [運算式](../cpp/expressions-cpp.md))。

- 逗號運算子的左運算元 (如需詳細資訊，請參閱 [逗號運算子](../cpp/comma-operator.md) )。

- 條件運算子 (`? :`) 的第二個或第三個運算元 (如需詳細資訊，請參閱 [含條件運算子的運算式](../cpp/conditional-operator-q.md) )。

下表說明類型大小的限制。 這些限制與 Microsoft 實作無關。

### <a name="fundamental-types-of-the-c-language"></a>C++ 語言的基本類型

|Category|類型|內容|
|--------------|----------|--------------|
|整數|**char**|類型**char**是一種整數類型，通常包含基本執行字元集的成員—根據預設，這是 Microsoft C++中的 ASCII。<br /><br /> 編譯器C++會將**char**、**帶正負**號的 char 和不**帶正負號 char**類型的變數視為具有不同的類型。 除非使用/J 編譯選項，否則**char**類型的變數會升級為**int** ，如同預設的類型**帶正負**號的 char。 在此情況下，它們會被視為不帶正負號的**char**類型，並在沒有簽署擴充的情況下升級為**int**|
||**bool**|類型**bool**是整數類資料類型，可以是下列兩個值的其中一個： **true**或**false**。 它的大小並未指定。|
||**short**|輸入**short int** （或簡稱**short**）是大於或等於**char**類型大小的整數類資料類型，而且短于或等於**int**類型的大小。<br /><br /> **Short**類型的物件可以宣告為**帶正負**號的簡短或不**帶正負**號的 short。 「**帶正負**號的簡短」是**short**的同義字。|
||**int**|**Int**類型是大於或等於類型**short int**大小的整數類資料類型，而且短于或等於**long**類型的大小。<br /><br /> **Int**類型的物件可以宣告為**帶正負**號的 int 或不**帶正負**號的 int。**帶正負**號的 int 是**int**的同義字。|
||**__int8**、 **__int16**、 **__int32**、 **__int64**|可調整大小的整數 `__int n`，其中 `n` 是整數變數的大小 (以位元為單位)。 **__int8**、 **__int16**、 **__int32**和 **__int64**是 Microsoft 專有的關鍵字。 並非所有類型都適用于所有架構。 （不支援 **__int128** ）。|
||**long**|**Long**類型（或**long int**）是大於或等於**int**類型大小的整數類資料類型。（在 Windows **long**的大小與**int**相同）。<br /><br /> **Long**類型的物件可以宣告為**帶正負**號的 long 或不**帶正負**號的 long。 **帶正負**號的 long 是**long**的同義字。|
||**long long**|大於不帶正負號的**長**整數。<br /><br /> **Long** long 類型的物件可以宣告為**帶正負**號的 long long 或不**帶正負**號的長長格式。 「**帶正負**號的長長時間」是**長**時間的同義字。|
||**wchar_t**， **__wchar_t**|**Wchar_t**類型的變數會指定寬字元或多位元組字元類型。 根據預設， **wchar_t**是原生類型，但是您可以使用[/zc： wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ，讓**wchar_t**不**帶正負號簡短**的 typedef。 **__Wchar_t**類型是原生**Wchar_t**類型的 Microsoft 特定同義字。<br /><br /> 在字元或字串常數之前使用 L 前置詞，指定寬字元類型。|
|浮點數|**float**|**Float**類型是最小的浮點類型。|
||**double**|**Double**類型是大於或等於**float**類型，但短于或等於**long double**類型大小的浮點類型。<br /><br /> Microsoft 專有： **long double**和**double**的表示方式完全相同。 不過， **long double**和**double**是不同的類型。|
||**long double**|**Long double**類型是大於或等於**double**類型的浮點類型。|

**Microsoft 專屬**

下表列出 Microsoft C++ 的基本類型所需的儲存空間量。

### <a name="sizes-of-fundamental-types"></a>基本類型的大小

|類型|大小|
|----------|----------|
|**bool**、 **char**、不**帶正負**號的 char、**帶正負**號的 char、 **__int8**|1 個位元組|
|**__int16**、**簡短**、不**帶正負**號的簡短、 **wchar_t**、 **__wchar_t**|2 個位元組|
|**float**、 **__int32**、 **int**、不**帶正負**號的 int、 **long**、不**帶正負**號的 long|4 個位元組|
|**double**、 **__int64**、 **long double**、 **long long**|8 個位元組|

**結束 Microsoft 專屬**

如需每個類型值範圍的摘要，請參閱 [資料類型範圍](../cpp/data-type-ranges.md) 。

如需類型轉換的詳細資訊，請參閱 [標準轉換](../cpp/standard-conversions.md)。

## <a name="see-also"></a>請參閱

[資料類型範圍](../cpp/data-type-ranges.md)