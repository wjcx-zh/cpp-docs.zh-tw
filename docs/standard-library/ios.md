---
title: '&lt;ios&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 8ba03e5ab5dd90a6f29e08b01576803a00f0bd24
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845480"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

定義 iostreams 作業的數個基本類型和函式。 此標頭通常會由其他 iostream 標頭為您納入；您很少會直接將其納入。

## <a name="requirements"></a>規格需求

**標頭**： \<ios>

**命名空間：** std

> [!NOTE]
> 連結 \<ios> 庫會使用 `#include <iosfwd>` 語句。

## <a name="remarks"></a>備註

操作工具由一個大型函式群組所組成。 中宣告的操作工具 \<ios> 改變了類別 [ios_base](../standard-library/ios-base-class.md)之引數物件中所儲存的值。 其他操作工具會對由此類別衍生之類型的物件所控制的資料流程執行動作，例如其中一個類別樣板的特製化 [basic_istream](../standard-library/basic-istream-class.md) 或 [basic_ostream](../standard-library/basic-ostream-class.md)。 例如， [noskipws](../standard-library/ios-functions.md#noskipws) (**Str**) 會清除物件中的格式旗標，該旗標 `ios_base::skipws` `str` 可以是下列其中一種類型。

基於針對衍生自 `ios_base` 的類別提供的特殊插入和擷取作業，您也可以將操作工具插入輸出資料流中，或從輸入資料流中加以擷取，以呼叫操作工具。 例如：

```cpp
istr>> noskipws;
```

會呼叫 [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**)。

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[Ios](../standard-library/ios-typedefs.md#ios)|支援來自舊 iostream 程式庫的 ios 類別。|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|支援內部作業。|
|[streampos](../standard-library/ios-typedefs.md#streampos)|保留緩衝區指標或檔案指標的目前位置。|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|指定資料流的大小。|
|[wios](../standard-library/ios-typedefs.md#wios)|支援來自舊 iostream 程式庫的 wios 類別。|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|保留緩衝區指標或檔案指標的目前位置。|

### <a name="manipulators"></a>操作工具

|名稱|描述|
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|指定 [bool](../cpp/bool-cpp.md) 類型的變數 **`true`** **`false`** 在資料流程中顯示為或。|
|[12 月](../standard-library/ios-functions.md#dec)|指定整數變數會以基底 10 標記法顯示。|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|設定 `ios_base` 物件的旗標會使用浮點值的預設顯示格式。|
|[固定](../standard-library/ios-functions.md#fixed)|指定浮點數會以固定十進位標記法顯示。|
|[hex](../standard-library/ios-functions.md#hex)|指定以基底 16 標記法顯示整數變數。|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|使數字的正負號靠左對齊，數字靠右對齊。|
|[離開](../standard-library/ios-functions.md#left)|使與輸出寬度不同寬的文字出現在具有左邊界的資料流排清中。|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 0 或 1。|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|關閉指出據以顯示數字之標記基底的功能。|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|顯示小數部分為零之浮點數的整數部分。|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|使正數不明確標示正負號。|
|[noskipws](../standard-library/ios-functions.md#noskipws)|使輸入資料流讀取空格。|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|使輸出在緩衝區已滿時進行緩衝處理和處理。|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|指定以小寫顯示十六進位數字和科學標記法中的指數。|
|[10月](../standard-library/ios-functions.md#oct)|指定以基底 8 標記法顯示整數變數。|
|[對](../standard-library/ios-functions.md#right)|使與輸出寬度不同寬的文字出現在具有右邊界的資料流排清中。|
|[科學](../standard-library/ios-functions.md#scientific)|使浮點數使用科學標記法顯示。|
|[showbase](../standard-library/ios-functions.md#showbase)|指出據以顯示數字的標記基底。|
|[showpoint](../standard-library/ios-functions.md#showpoint)|顯示浮點數的整數部分和小數點右側的數字，即使小數部分為零亦然。|
|[showpos](../standard-library/ios-functions.md#showpos)|使正數明確標示正負號。|
|[skipws](../standard-library/ios-functions.md#skipws)|使輸入資料流不讀取空格。|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|使輸出在緩衝區不為空時進行處理。|
|[大寫](../standard-library/ios-functions.md#uppercase)|指定以大寫顯示十六進位數字和科學標記法中的指數。|

### <a name="error-reporting"></a>錯誤報告

|名稱|描述|
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|類別樣板描述類別樣板 (之輸入資料流程的一般儲存和成員函式 [basic_istream](../standard-library/basic-istream-class.md)) 以及相依于樣板參數之類別樣板 [basic_ostream](../standard-library/basic-ostream-class.md)) 的輸出資料流程 (。|
|[fpos](../standard-library/fpos-class.md)|類別樣板描述的物件可儲存在任何資料流程中還原任意檔案位置指標所需的所有資訊。|
|[ios_base](../standard-library/ios-base-class.md)|此類別說明未依存於範本參數的輸入和輸出資料流通用的儲存體和成員函式。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
