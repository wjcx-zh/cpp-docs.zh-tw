---
title: 內建類型（c + +）
ms.date: 07/22/2020
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
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
ms.openlocfilehash: 73486dd4d81fc91007f078ec5c509bcb963d2706
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232270"
---
# <a name="built-in-types-c"></a>內建類型（c + +）

內建類型（也稱為*基本類型*）是由 c + + 語言標準所指定，並內建于編譯器中。 內建類型並未定義于任何標頭檔中。 內建類型分為三個主要類別：*整數*、*浮點數*和*void*。 整數類資料類型代表整數。 浮點類型可以指定可能有小數部分的值。 編譯器會將大部分的內建類型視為不同的類型。 不過，某些類型是*同義字*，或由編譯器視為對等類型。

## <a name="void-type"></a>Void 類型

此 [`void`](void-cpp.md) 類型描述一組空的值。 無法指定類型的變數 **`void`** 。 **`void`** 類型主要是用來宣告不傳回任何值的函式，或宣告不具類型或任意類型資料的泛型指標。 任何運算式都可以明確轉換或轉換成類型 **`void`** 。 不過，這類運算式僅限於下列用法：

- 運算陳述式 （如需詳細資訊，請參閱[運算式](expressions-cpp.md)）。

- 逗號運算子的左運算元 （如需詳細資訊，請參閱[逗號運算子](comma-operator.md)）。

- 條件運算子 (`? :`) 的第二個或第三個運算元 （如需詳細資訊，請參閱[具有條件運算子的運算式](conditional-operator-q.md)）。

## <a name="stdnullptr_t"></a>std：： nullptr_t

關鍵字 **`nullptr`** 是類型的 null 指標常數 `std::nullptr_t` ，可以轉換成任何原始指標類型。 如需詳細資訊，請參閱 [`nullptr`](nullptr.md)。

## <a name="boolean-type"></a>布林值類型

[`bool`](bool-cpp.md)型別可以具有值 [`true`](../cpp/true-cpp.md) 和 [`false`](../cpp/false-cpp.md) 。 類型的大小 **`bool`** 為「執行特定」。 如需 Microsoft 特定的執行詳細資料，請參閱[內建類型的大小](#sizes-of-built-in-types)。

## <a name="character-types"></a>字元類型

**`char`** 型別是字元表示型別，可有效率地將基本執行字元集的成員編碼。 C + + 編譯器會將類型為、和的變數視為 **`char`** **`signed char`** **`unsigned char`** 具有不同的類型。

**Microsoft 專有**： **`char`** **`int`** **`signed char`** 除非使用編譯選項，否則類型的變數會升級為，如同從類型的預設值一樣 [`/J`](../build/reference/j-default-char-type-is-unsigned.md) 。 在此情況下，它們會被視為型別 **`unsigned char`** ，而且會升級為 **`int`** 不含正負號的延伸。

類型的變數 **`wchar_t`** 是寬字元或多位元組字元類型。 在 **`L`** 字元或字串常值之前使用前置詞，以指定寬字元類型。

**Microsoft 特定**：根據預設， **`wchar_t`** 是原生類型，但您可以使用 [`/Zc:wchar_t-`](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 來建立 **`wchar_t`** 的 typedef **`unsigned short`** 。 **`__wchar_t`** 類型是適用于原生類型的 Microsoft 特定同義字 **`wchar_t`** 。

**`char8_t`** 類型會用於 utf-8 字元標記法。 它與具有相同的標記法 **`unsigned char`** ，但編譯器會將其視為不同的類型。 **`char8_t`** 類型在 c + + 20 中是新的。 **Microsoft 專有**：使用 **`char8_t`** 需要 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 編譯器選項。

**`char16_t`** 類型用於 utf-16 字元標記法。 它必須夠大，才能代表任何 UTF-16 程式碼單位。 編譯器會將它視為不同的類型。

**`char32_t`** 類型用於 UTF-32 字元標記法。 它必須夠大，才能代表任何 UTF-32 程式碼單位。 編譯器會將它視為不同的類型。

## <a name="floating-point-types"></a>浮點類型

浮點類型會使用 IEEE-754 標記法，來提供範圍廣泛巨量的分數值近似值。 下表列出 c + + 中的浮點類型，以及浮點類型大小的比較限制。 這些限制是由 c + + 標準所規定，而且與 Microsoft 的實行無關。 標準中不會指定內建浮點類型的絕對大小。

| 類型 | 目錄 |
|--|--|
| **`float`** | 類型 **`float`** 是 c + + 中最小的浮點類型。 |
| **`double`** | 類型 **`double`** 是大於或等於類型 **`float`** ，但短于或等於類型大小的浮點類型 **`long double`** 。 |
| **`long double`** | 類型 **`long double`** 是大於或等於類型的浮點類型 **`double`** 。 |

**Microsoft 特定**：和的表示方式 **`long double`** **`double`** 完全相同。 不過， **`long double`** **`double`** 編譯器會將和視為不同的類型。 Microsoft c + + 編譯器會使用4和8個位元組的 IEEE-754 浮點標記法。 如需詳細資訊，請參閱[IEEE 浮點標記法](../build/ieee-floating-point-representation.md)。

## <a name="integer-types"></a>整數類型

此 **`int`** 類型是預設的基本整數類型。 它可以代表實值範圍內的所有整數。

*帶*正負號的整數標記法是可以同時保留正值和負值的值。 根據預設，或當修飾詞關鍵字存在時，會使用它 **`signed`** 。 **`unsigned`** 修飾詞關鍵字指定只能保存非負數值的不*帶正負*號表示。

大小修飾詞會指定所使用之整數表示的寬度（以位為單位）。 語言支援 **`short`** 、 **`long`** 和修飾詞 **`long long`** 。 **`short`** 類型必須至少有16位寬。 **`long`** 類型必須至少為32位寬。 **`long long`** 類型必須至少為64位寬。 標準會指定整數類型之間的大小關聯性：

`1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)`

執行必須同時維護每個類型的最小大小需求和大小關聯性。 不過，實際的大小可能和在不同的執行之間有所不同。 如需 Microsoft 特定的執行詳細資料，請參閱[內建類型的大小](#sizes-of-built-in-types)。

**`int`** 當 **`signed`** 指定、或大小修飾詞時，可能會省略關鍵字 **`unsigned`** 。 修飾詞和 **`int`** 類型（如果有的話）可能會以任何順序出現。 例如， **`short unsigned`** 和會 **`unsigned int short`** 參考相同的類型。

### <a name="integer-type-synonyms"></a>整數類型同義字

編譯器會將下列類型群組視為同義字：

- **`short`**, **`short int`**, **`signed short`**, **`signed short int`**

- **`unsigned short`**, **`unsigned short int`**

- **`int`**, **`signed`**, **`signed int`**

- **`unsigned`**, **`unsigned int`**

- **`long`**, **`long int`**, **`signed long`**, **`signed long int`**

- **`unsigned long`**, **`unsigned long int`**

- **`long long`**, **`long long int`**, **`signed long long`**, **`signed long long int`**

- **`unsigned long long`**, **`unsigned long long int`**

**Microsoft 特定**的整數類型包含特定寬度 **`__int8`** 、 **`__int16`** 、 **`__int32`** 和 **`__int64`** 類型。 這些類型可以使用和修飾詞 **`signed`** **`unsigned`** 。 **`__int8`** 資料類型與類型同義，是與類型同義、與類型同義， **`char`** **`__int16`** 而且與 **`short`** **`__int32`** **`int`** **`__int64`** 類型同義 **`long long`** 。

## <a name="sizes-of-built-in-types"></a>內建類型的大小

大部分的內建類型都具有實作為定義的大小。 下表列出 Microsoft c + + 內建類型所需的儲存空間數量。 特別是， **`long`** 即使在64位作業系統上，也是4個位元組。

| 類型 | 大小 |
|--|--|
| **`bool`**, **`char`**, **`char8_t`**, **`unsigned char`**, **`signed char`**, **`__int8`** | 1 個位元組 |
| **`char16_t`**, **`__int16`**, **`short`**, **`unsigned short`**, **`wchar_t`**, **`__wchar_t`** | 2 個位元組 |
| **`char32_t`**, **`float`**, **`__int32`**, **`int`**, **`unsigned int`**, **`long`**, **`unsigned long`** | 4 個位元組 |
| **`double`**, **`__int64`**, **`long double`**, **`long long`**, **`unsigned long long`** | 8 個位元組 |

如需每個類型值範圍的摘要，請參閱[資料類型範圍](data-type-ranges.md)。

如需類型轉換的詳細資訊，請參閱[標準轉換](standard-conversions.md)。

## <a name="see-also"></a>另請參閱

[資料類型範圍](data-type-ranges.md)
