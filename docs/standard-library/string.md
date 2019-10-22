---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 0b8ca5744418860cc6b4868dda9174ae2eb68a98
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685897"
---
# <a name="ltstringgt"></a>&lt;string&gt;

定義容器類別範本 `basic_string` 和各種支援的範本。

如需 `basic_string` 的詳細資訊，請參閱 [basic_string Class](../standard-library/basic-string-class.md)。

## <a name="syntax"></a>語法

```cpp
#include <string>
```

## <a name="remarks"></a>備註

C++ 語言和 C++ 標準程式庫支援兩種字串類型：

- 以 Null 結束的字元陣列，通常稱為 C 字串。

- 類型為 `basic_string` 的類別樣板物件，可處理所有類似**char**的範本引數。

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|一種類型，描述類別樣板的特製化，`basic_string` 以**char**類型的元素做為 `string`。|
|[wstring](../standard-library/string-typedefs.md#wstring)|一種類型，描述類別樣板的特製化，`basic_string` 以**wchar_t**的元素做為 `wstring`。|
|[u16string](../standard-library/string-typedefs.md#u16string)|一種類型，描述類別樣板的特製化，`basic_string` 以 `char16_t` 類型的元素為基礎。|
|[u32string](../standard-library/string-typedefs.md#u32string)|一種類型，描述類別樣板的特製化，`basic_string` 以 `char32_t` 類型的元素為基礎。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator+](../standard-library/string-operators.md#op_add)|串連兩個字串物件。|
|[operator!=](../standard-library/string-operators.md#op_neq)|測試運算子左邊的字串物件是否不等於右邊的字串物件。|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|測試運算子左邊的字串物件是否等於右邊的字串物件。|
|[operator<](../standard-library/string-operators.md#op_lt)|測試運算子左邊的字串物件是否小於右邊的字串物件。|
|[operator<=](../standard-library/string-operators.md#op_lt_eq)|測試運算子左邊的字串物件是否小於或等於右邊的字串物件。|
|[operator<\<](../standard-library/string-operators.md#op_lt_lt)|將字串插入至輸出資料流的範本函式。|
|[operator>](../standard-library/string-operators.md#op_gt)|測試運算子左邊的字串物件是否大於右邊的字串物件。|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|測試運算子左邊的字串物件是否大於或等於右邊的字串物件。|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|從輸入資料流擷取字串的範本函式。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|||
|-|-|
|雜湊|產生字串的雜湊。|
|[swap](../standard-library/string-functions.md#swap)|交換兩個字串的字元陣列。|
|[stod](../standard-library/string-functions.md#stod)|將字元序列轉換成**雙精度浮點數**。|
|[stof](../standard-library/string-functions.md#stof)|將字元序列轉換成**float**。|
|[stoi](../standard-library/string-functions.md#stoi)|將字元序列轉換為整數。|
|[stold](../standard-library/string-functions.md#stold)|將字元序列轉換成**長雙精度浮點數**。|
|[stoll](../standard-library/string-functions.md#stoll)|將字元序列轉換成**長長**的。|
|[stoul](../standard-library/string-functions.md#stoul)|將字元序列轉換成不**帶正負**號的長整數。|
|[stoull](../standard-library/string-functions.md#stoull)|將字元序列轉換成不**帶正負**號的長整數。|
|[to_string](../standard-library/string-functions.md#to_string)|將值轉換成 `string`。|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|將值轉換成寬 `string`。|

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[getline 範本](../standard-library/string-functions.md#getline)|從輸入資料流一行一行地擷取字串。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[basic_string 類別](../standard-library/basic-string-class.md)|類別樣板，描述可以儲存任意類似字元之物件序列的物件。|
|[char_traits 結構](../standard-library/char-traits-struct.md)|類別範本，描述與 CharType 類型的字元相關聯的屬性。|

### <a name="specializations"></a>特製化

|||
|-|-|
|[char_traits\<char> 結構](../standard-library/char-traits-char-struct.md)|結構，會將樣板結構 `char_traits`\<CharType> 特製化為 `char` 類型的項目。|
|[char_traits<wchar_t> 結構](../standard-library/char-traits-wchar-t-struct.md)|結構，會將樣板結構 `char_traits`\<CharType> 特製化為 `wchar_t` 類型的項目。|
|[char_traits<char16_t> 結構](../standard-library/char-traits-char16-t-struct.md)|結構，會將樣板結構 `char_traits`\<CharType> 特製化為 `char16_t` 類型的項目。|
|[char_traits<char32_t> 結構](../standard-library/char-traits-char32-t-struct.md)|結構，會將樣板結構 `char_traits`\<CharType> 特製化為 `char32_t` 類型的項目。|

## <a name="requirements"></a>需求

- **標頭：** \<string>

- **命名空間:** std

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
