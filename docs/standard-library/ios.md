---
title: '&lt;ios&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ios>
- ios/std::<ios>
dev_langs:
- C++
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fce633707096db8913da6d3601da20d14d3704c7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961479"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

定義 iostreams 作業的數個基本類型和函式。 此標頭通常會由其他 iostream 標頭為您納入；您很少會直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <ios>

```

## <a name="remarks"></a>備註

操作工具由一個大型函式群組所組成。 在 \<ios> 中宣告的操作工具會改變儲存在其 [ios_base](../standard-library/ios-base-class.md) 類別之引數物件中的值。 其他操作工具會對由此類別衍生之類型的物件所控制的資料流執行動作，例如 [basic_istream](../standard-library/basic-istream-class.md) 或 [basic_ostream](../standard-library/basic-ostream-class.md) 其中一種範本類別的特製化。 例如， [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) 清除的格式旗標`ios_base::skipws`物件中`str`，這可以是其中一種類型。

基於針對衍生自 `ios_base` 的類別提供的特殊插入和擷取作業，您也可以將操作工具插入輸出資料流中，或從輸入資料流中加以擷取，以呼叫操作工具。 例如: 

```cpp
istr>> noskipws;
```

會呼叫 [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**)。

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[ios](../standard-library/ios-typedefs.md#ios)|支援來自舊 iostream 程式庫的 ios 類別。|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|支援內部作業。|
|[streampos](../standard-library/ios-typedefs.md#streampos)|保留緩衝區指標或檔案指標的目前位置。|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|指定資料流的大小。|
|[wios](../standard-library/ios-typedefs.md#wios)|支援來自舊 iostream 程式庫的 wios 類別。|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|保留緩衝區指標或檔案指標的目前位置。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 **true** 或 **false**。|
|[dec](../standard-library/ios-functions.md#dec)|指定整數變數會以基底 10 標記法顯示。|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|設定 `ios_base` 物件的旗標會使用浮點值的預設顯示格式。|
|[fixed](../standard-library/ios-functions.md#fixed)|指定浮點數會以固定十進位標記法顯示。|
|[hex](../standard-library/ios-functions.md#hex)|指定以基底 16 標記法顯示整數變數。|
|[internal](../standard-library/ios-functions.md#internal)|使數字的正負號靠左對齊，數字靠右對齊。|
|[left](../standard-library/ios-functions.md#left)|使與輸出寬度不同寬的文字出現在具有左邊界的資料流排清中。|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 0 或 1。|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|關閉指出據以顯示數字之標記基底的功能。|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|顯示小數部分為零之浮點數的整數部分。|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|使正數不明確標示正負號。|
|[noskipws](../standard-library/ios-functions.md#noskipws)|使輸入資料流讀取空格。|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|使輸出在緩衝區已滿時進行緩衝處理和處理。|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|指定以小寫顯示十六進位數字和科學標記法中的指數。|
|[oct](../standard-library/ios-functions.md#oct)|指定以基底 8 標記法顯示整數變數。|
|[right](../standard-library/ios-functions.md#right)|使與輸出寬度不同寬的文字出現在具有右邊界的資料流排清中。|
|[scientific](../standard-library/ios-functions.md#scientific)|使浮點數使用科學標記法顯示。|
|[showbase](../standard-library/ios-functions.md#showbase)|指出據以顯示數字的標記基底。|
|[showpoint](../standard-library/ios-functions.md#showpoint)|顯示浮點數的整數部分和小數點右側的數字，即使小數部分為零亦然。|
|[showpos](../standard-library/ios-functions.md#showpos)|使正數明確標示正負號。|
|[skipws](../standard-library/ios-functions.md#skipws)|使輸入資料流不讀取空格。|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|使輸出在緩衝區不為空時進行處理。|
|[uppercase](../standard-library/ios-functions.md#uppercase)|指定以大寫顯示十六進位數字和科學標記法中的指數。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|此範本類別描述依存於範本參數的輸入資料流 (屬於範本類別 [basic_istream](../standard-library/basic-istream-class.md)) 和輸出資料流 (屬於範本類別 [basic_ostream](../standard-library/basic-ostream-class.md)) 通用的儲存體和成員函式。|
|[fpos](../standard-library/fpos-class.md)|此範本類別說明可儲存對任何資料流內的任意檔案位置指標進行還原之所有必要資訊的物件。|
|[ios_base](../standard-library/ios-base-class.md)|此類別說明未依存於範本參數的輸入和輸出資料流通用的儲存體和成員函式。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
