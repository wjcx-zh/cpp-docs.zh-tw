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
ms.openlocfilehash: 8e9675a673462c8eaab94d29a3ae36a4786737b7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687859"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定義類別樣板 basic_istream，它會調節 iostreams 的提取，而類別樣板 basic_iostream 則會同時調節插入和提取。 標頭也會定義相關的操作工具。 此標頭檔通常會由其他 iostreams 標頭為您納入；您很少需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|類型 `basic_iostream` 在**char**上特製化。|
|[istream](../standard-library/istream-typedefs.md#istream)|類型 `basic_istream` 在**char**上特製化。|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|針對 **wchar** 特殊化的 `basic_iostream` 類型。|
|[wistream](../standard-library/istream-typedefs.md#wistream)|針對 **wchar** 特殊化的 `basic_istream` 類型。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|略過資料流中的空白字元。|
|[swap](../standard-library/istream-functions.md#istream_swap)|交換兩個資料流物件。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|從資料流中擷取字元和字串。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可執行輸入和輸出的資料流類別。|
|[basic_istream](../standard-library/basic-istream-class.md)|類別樣板所描述的物件，可控制從資料流程緩衝區的專案和編碼物件的提取，其中包含 `Elem` 類型的專案（也稱為[char_type](../standard-library/basic-ios-class.md#char_type)），其字元特性是由類別 `Tr` 所決定，也稱為[traits_type](../standard-library/basic-ios-class.md#traits_type)。|

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
