---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 47924c3d6bd1a2f45cdbac648f4f563c57ce8939
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459110"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

定義類別`basic_string_view`樣板和相關的類型和運算子。 (需要編譯器選項[std: c + + 17](../build/reference/std-specify-language-standard-version.md)或更新版本)。

## <a name="syntax"></a>語法

```cpp
#include <string_view>
```

## <a name="remarks"></a>備註

String_view 的範本特製化系列提供有效率的方式, 將唯讀、例外狀況安全的非主控控制碼傳遞至任何類似字串之物件的字元資料, 並在位置為零的序列的第一個元素。 類型`string_view`的函式參數 (這是的`basic_string_view<char>`typedef) `std::string`可以接受引數, 例如、 **char\*** 或任何其他類似字串的窄字元類別, 以隱含轉換成`string_view`已定義。 同樣地, 的`wstring_view` `u16string_view`參數或`u32string_view`可以接受已定義隱含轉換的任何字串類型。 如需詳細資訊, 請參閱[Basic_string_view 類別](../standard-library/basic-string-view-class.md)。

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|類別`basic_string_view`樣板的特製化, 其中包含**char**類型的元素。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|類別`basic_string_view`樣板的特製化, 其中包含**wchar_t**類型的元素。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|`basic_string_view`具有類型`char16_t`之元素的類別樣板特製化。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|`basic_string_view`具有類型`char32_t`之元素的類別樣板特製化。|

### <a name="operators"></a>運算子

String_view > 運算子可以將物件與任何可轉換之字串類型的物件相比較`string_view`。 \<

|運算子|描述|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|測試運算子左邊的物件是否不等於右邊的物件。|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|測試運算子左邊的物件是否等於右邊的物件。|
|[operator<](../standard-library/string-view-operators.md#op_lt)|測試運算子左邊的物件是否小於右邊的物件 (object)。|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|測試運算子左邊的物件是否小於或等於右邊的物件。|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|將插入`string_view`至輸出資料流程的範本函式。|
|[operator>](../standard-library/string-view-operators.md#op_gt)|測試運算子左邊的物件是否大於右邊的物件的位置。|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|測試運算子左邊的物件是否大於或等於右邊的物件。|

### <a name="literals"></a>常值

|運算子|說明|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|根據附加的字串`u16string_view`常值`u32string_view`型別`wstring_view` `string_view`, 來構造、、或。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_string_view 類別](../standard-library/basic-string-view-class.md)|類別樣板, 提供唯讀的視圖給任意類似字元的物件序列。|
|[hash](string-view-hash.md)|為 string_view 產生雜湊值的函式物件。|

## <a name="requirements"></a>需求

- **標頭:** \<string_view >

- **命名空間：** std

- **編譯器選項:** std: c + + 17 (或更新版本)

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
