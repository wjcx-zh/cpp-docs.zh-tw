---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 37399bb50f195c683b52eea4c8fadf8679d62852
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233089"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定義 basic_istream 的類別樣板，它會調節 iostreams 的提取，而 basic_iostream 會協調插入和提取的類別樣板。 標頭也會定義相關的操作工具。 此標頭檔通常會由其他 iostreams 標頭為您納入；您很少需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|特製化的型別 `basic_iostream` **`char`** 。|
|[istream](../standard-library/istream-typedefs.md#istream)|特製化的型別 `basic_istream` **`char`** 。|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|針對 **wchar** 特殊化的 `basic_iostream` 類型。|
|[wistream](../standard-library/istream-typedefs.md#wistream)|針對 **wchar** 特殊化的 `basic_istream` 類型。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[atl-ws-01](../standard-library/istream-functions.md#ws)|略過資料流中的空白字元。|
|[調換](../standard-library/istream-functions.md#istream_swap)|交換兩個資料流物件。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子>>](../standard-library/istream-operators.md#op_gt_gt)|從資料流中擷取字元和字串。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可執行輸入和輸出的資料流類別。|
|[basic_istream](../standard-library/basic-istream-class.md)|類別樣板描述的物件可控制從資料流程緩衝區的專案和編碼物件的提取，其中包含類型的元素 `Elem` （也稱為[char_type](../standard-library/basic-ios-class.md#char_type)），其字元特性是由類別 `Tr` （也稱為[traits_type](../standard-library/basic-ios-class.md#traits_type)）所決定。|

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
