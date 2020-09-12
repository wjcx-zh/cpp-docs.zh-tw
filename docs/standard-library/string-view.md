---
title: '&lt;string_view&gt;'
description: 概述， `basic_string_view` 它是指類似 char 物件的常數連續序列。
ms.date: 9/4/2020
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: f74f6c5855f71b0df46f585e874002cdb4308e42
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039907"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

定義類別範本 `basic_string_view` 以及相關類型和運算子。  (需要編譯器選項 [std： c + + 17](../build/reference/std-specify-language-standard-version.md) 或更新版本。 ) 

## <a name="syntax"></a>語法

```cpp
#include <string_view>
```

## <a name="remarks"></a>備註

樣板特製化 `string_view` 系列提供有效的方式，可將唯讀、例外狀況安全、非擁有的控制碼傳遞至在位置為零之序列的第一個專案。  (類型的函式參數，也 `string_view` 就是) 的 typedef `basic_string_view<char>` 可以接受引數 `std::string` ，例如、 `char*` 或任何其他類似字串的縮小字元類別，以定義隱含轉換 `string_view` 。 同樣地，或的參數也 `wstring_view` `u16string_view` `u32string_view` 可以接受任何已定義隱含轉換的字串類型。 如需詳細資訊，請參閱 [Basic_string_view 類別](../standard-library/basic-string-view-class.md)。

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|類別樣板的特製化 `basic_string_view` ，其具有類型的元素 **`char`** 。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|類別樣板的特製化 `basic_string_view` ，其具有類型的元素 **`wchar_t`** 。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|類別樣板的特製化 `basic_string_view` ，其具有類型的元素 **`char16_t`** 。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|類別樣板的特製化 `basic_string_view` ，其具有類型的元素 **`char32_t`** 。|

### <a name="operators"></a>操作員

這些 \<string_view> 運算子可以比較 `string_view` 物件與任何可轉換的字串類型的物件。

|運算子|描述|
|-|-|
|[operator！ =](../standard-library/string-view-operators.md#op_neq)|測試運算子左邊的物件是否不等於右邊的物件。|
|[operator = =](../standard-library/string-view-operators.md#op_eq_eq)|測試運算子左邊的物件是否等於右邊的物件。|
|[運算子<](../standard-library/string-view-operators.md#op_lt)|測試運算子左邊的物件是否小於右邊的物件（object）。|
|[運算子<=](../standard-library/string-view-operators.md#op_lt_eq)|測試運算子左邊的物件是否小於或等於右邊的物件。|
|[運算子<\<](../standard-library/string-view-operators.md#op_lt_lt)|將插入至輸出資料流程的範本函式 `string_view` 。|
|[運算子>](../standard-library/string-view-operators.md#op_gt)|測試運算子左邊的物件是否大於右邊的物件（object）。|
|[運算子>=](../standard-library/string-view-operators.md#op_gt_eq)|測試運算子左邊的物件是否大於或等於右邊的物件。|

### <a name="literals"></a>常值

|運算子|描述|
|-|-|
|[Sv](../standard-library/string-view-operators.md#op_sv)|`string_view` `wstring_view` `u16string_view` `u32string_view` 根據附加的字串常值型別，來建立、、或。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_string_view 類別](../standard-library/basic-string-view-class.md)|類別樣板，提供唯讀的視圖給任意類似字元的物件序列。|
|[hash](string-view-hash.md)|產生 string_view 雜湊值的函式物件。|

## <a name="requirements"></a>需求

- **標頭：**\<string_view>

- **命名空間：** std

- **編譯器選項：** [std： c + + 17](../build/reference/std-specify-language-standard-version.md) 或更新版本。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
