---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 13b6f5c63b9426fc4c31527f0d1ae8291d07807f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222208"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

定義類別樣板 `basic_string_view` 和相關的類型和運算子。 （需要編譯器選項[std： c + + 17](../build/reference/std-specify-language-standard-version.md)或更新版本）。

## <a name="syntax"></a>語法

```cpp
#include <string_view>
```

## <a name="remarks"></a>備註

String_view 系列的範本特製化提供有效率的方式，將唯讀、例外狀況安全、非擁有的控制碼傳遞至任何類似字串之物件的字元資料，並在位置為零的序列的第一個元素。 類型的函式參數 `string_view` （這是的 typedef `basic_string_view<char>` ）可以接受引數，例如 `std::string` 、 **char \* **或任何其他類似字串的窄字元類別，以定義隱含的轉換 `string_view` 。 同樣地，的參數 `wstring_view` `u16string_view` 或 `u32string_view` 可以接受已定義隱含轉換的任何字串類型。 如需詳細資訊，請參閱[Basic_string_view 類別](../standard-library/basic-string-view-class.md)。

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|具有類型之元素的類別樣板特製化 `basic_string_view` **`char`** 。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|具有類型之元素的類別樣板特製化 `basic_string_view` **`wchar_t`** 。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|具有類型之元素的類別樣板特製化 `basic_string_view` **`char16_t`** 。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|具有類型之元素的類別樣板特製化 `basic_string_view` **`char32_t`** 。|

### <a name="operators"></a>操作員

\<string_view>運算子可以比較 `string_view` 物件與任何可轉換之字串類型的物件。

|運算子|描述|
|-|-|
|[operator！ =](../standard-library/string-view-operators.md#op_neq)|測試運算子左邊的物件是否不等於右邊的物件。|
|[operator = =](../standard-library/string-view-operators.md#op_eq_eq)|測試運算子左邊的物件是否等於右邊的物件。|
|[運算子<](../standard-library/string-view-operators.md#op_lt)|測試運算子左邊的物件是否小於右邊的物件（object）。|
|[運算子<=](../standard-library/string-view-operators.md#op_lt_eq)|測試運算子左邊的物件是否小於或等於右邊的物件。|
|[運算子<\<](../standard-library/string-view-operators.md#op_lt_lt)|將插入 `string_view` 至輸出資料流程的範本函式。|
|[運算子>](../standard-library/string-view-operators.md#op_gt)|測試運算子左邊的物件是否大於右邊的物件的位置。|
|[運算子>=](../standard-library/string-view-operators.md#op_gt_eq)|測試運算子左邊的物件是否大於或等於右邊的物件。|

### <a name="literals"></a>常值

|運算子|描述|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|`string_view` `wstring_view` `u16string_view` `u32string_view` 根據附加的字串常值型別，來構造、、或。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_string_view 類別](../standard-library/basic-string-view-class.md)|類別樣板，提供唯讀的視圖給任意類似字元的物件序列。|
|[hash](string-view-hash.md)|產生 string_view 雜湊值的函式物件。|

## <a name="requirements"></a>需求

- **標頭：**\<string_view>

- **命名空間：** std

- **編譯器選項：** std： c + + 17 （或更新版本）

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
