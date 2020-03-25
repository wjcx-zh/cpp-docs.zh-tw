---
title: 資料類型範圍
ms.date: 05/07/2019
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: 8b4031eccccb432342790fef4da809542e77d669
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180260"
---
# <a name="data-type-ranges"></a>資料類型範圍

Microsoft C++ 32 位和64位編譯器會辨識本文稍後的表格中的類型。

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` （`unsigned long long`）

如果其名稱開頭為兩個底線 (`__`)，則資料類型是非標準的。

下表中指定的範圍是兩端皆包含。

|類型名稱|位元組|其他名稱|值的範圍|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**signed**|-2,147,483,648 至 2,147,483,647|
|**unsigned int**|4|**unsigned**|0 到 4,294,967,295|
|**__int8**|1|**char**|-128 到 127|
|**不帶正負號的 __int8**|1|**unsigned char**|0 至 255|
|**__int16**|2|**short**、 **short int**、**帶正負號的 short int**|-32,768 至 32,767|
|**不帶正負號的 __int16**|2|**無符號簡短**、不**帶正負號的短整數**|0 到 65,535|
|**__int32**|4|**帶正負**號、**帶正負**號的 int、 **int**|-2,147,483,648 至 2,147,483,647|
|**不帶正負號的 __int32**|4|**無符號**、不**帶正負**號的整數|0 到 4,294,967,295|
|**__int64**|8|**長**長、**帶正負**號的長長|-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807|
|**unsigned __int64**|8|**不帶正負號的長長**|0 到 18,446,744,073,709,551,615|
|**bool**|1|無|**false**或**true**|
|**char**|1|無|-預設為-128 到127<br /><br /> 使用 [/J](../build/reference/j-default-char-type-is-unsigned.md) 編譯時為 0 至 255|
|**帶正負號的字元**|1|無|-128 到 127|
|**unsigned char**|1|無|0 至 255|
|**short**|2|**short int**，**帶正負號的 short int**|-32,768 至 32,767|
|**unsigned short**|2|**unsigned short int**|0 到 65,535|
|**long**|4|**long int**，**帶正負號的 long int**|-2,147,483,648 至 2,147,483,647|
|**unsigned long**|4|**unsigned long int**|0 到 4,294,967,295|
|**long long**|8|無（但相當於 **__int64**）|-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807|
|**不帶正負號的長長**|8|無（但等同于不**帶正負**號的 __int64）|0 到 18,446,744,073,709,551,615|
|**enum**|視情況而異|無| |
|**float**|4|無|3.4E +/- 38 (7 位數)|
|**double**|8|無|1.7E +/- 308 (15 位數)|
|**long double**|與**double**相同|無|與**double**相同|
|**wchar_t**|2|**__wchar_t**|0 到 65,535|

視使用的方式而定， **__wchar_t**的變數會指定寬字元類型或多位元組字元類型。 在字元或字串常數之前使用 `L` 前置詞可指定寬字元類型常數。

**帶正負**號和不**帶正負**號的是可搭配任何整數類型使用的修飾詞，但**bool**除外。 請注意， **char**、**帶正負**號的字元和不**帶正負**號的字元是三種不同類型，用於多載和範本等機制。

**Int**和不**帶正負號 int**類型的大小為四個位元組。 不過，可移植程式碼不應該相依于**int**的大小，因為語言標準允許這種情況是實作為特定。

Visual Studio 中的 C/C++ 也支援具大小的整數類型。 如需詳細資訊，請參閱 [__int8、\___int16、\___int32、\___int64](../cpp/int8-int16-int32-int64.md) 和[整數限制](../cpp/integer-limits.md)。

如需每個類型之大小限制的詳細資訊，請參閱[內建類型](../cpp/fundamental-types-cpp.md)。

列舉類型的範圍會根據語言內容和指定的編譯器旗標而變更。 如需詳細資訊，請參閱 [C 列舉宣告](../c-language/c-enumeration-declarations.md) 和 [列舉](../cpp/enumerations-cpp.md)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[內建類型](../cpp/fundamental-types-cpp.md)
