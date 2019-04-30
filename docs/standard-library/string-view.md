---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 8952416cf37fc4d8d281d6ced9b8264495ec3799
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346976"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

定義類別樣板`basic_string_view`和相關類型及運算子。 (需要編譯器選項[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)或更新版本。)

## <a name="syntax"></a>語法

```cpp
#include <string_view>
```

## <a name="remarks"></a>備註

樣板特製化的 string_view 系列提供有效率的方式，將唯讀、 例外狀況安全、 非主控的控制代碼傳遞至任何類似字串的物件的字元資料的第一個元素的位置為零的順序。 函式參數的型別`string_view`(也就是 typedef `basic_string_view<char>`) 可以接受引數，例如`std::string`， **char\***，或窄字元的任何其他字串類似類別隱含轉換成`string_view`定義。 同樣地的參數`wstring_view`，`u16string_view`或`u32string_view`可接受為其定義的隱含轉換的任何字串類型。 如需詳細資訊，請參閱 < [basic_string_view 類別](../standard-library/basic-string-view-class.md)。

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|類別樣板的特製化`basic_string_view`類型的項目**char**。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|類別樣板的特製化`basic_string_view`類型的項目**wchar_t**。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|類別樣板的特製化`basic_string_view`類型的項目`char16_t`。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|類別樣板的特製化`basic_string_view`類型的項目`char32_t`。|

### <a name="operators"></a>運算子

\<String_view > 運算子可以比較`string_view`物件之任何轉換物件的字串類型。

|運算子|描述|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|測試運算子左邊的物件是否不等於右邊的物件。|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|測試運算子左邊的物件是否等於右邊的物件。|
|[operator<](../standard-library/string-view-operators.md#op_lt)|測試運算子左邊的物件為小於右邊的物件。|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|測試運算子左邊的物件是否小於或等於右邊的物件。|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|插入的範本函式`string_view`輸出資料流中。|
|[operator>](../standard-library/string-view-operators.md#op_gt)|測試運算子左邊的物件大於右邊的物件。|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|測試運算子左邊的物件是否大於或等於右邊的物件。|

### <a name="literals"></a>常值

|運算子|描述|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|建構`string_view`， `wstring_view`， `u16string_view`，或`u32string_view`根據它附加的字串常值類型。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_string_view 類別](../standard-library/basic-string-view-class.md)|類別樣板，提供一連串任意類似字元的物件的唯讀檢視。|
|[hash](string-view-hash.md)|產生 string_view 的雜湊值的函式物件。|

## <a name="requirements"></a>需求

- **標頭：** \<string_view >

- **命名空間：** std

- **編譯器選項：** /std: c + + 17 （或更新版本）

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
