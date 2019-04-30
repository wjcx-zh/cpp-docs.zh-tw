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
ms.openlocfilehash: 2e39c0de5b11c9aa0a4c69f0142841469ef798c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413277"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定義範本類別 basic_istream，以調解 iostreams 的擷取，並定義範本類別 basic_iostream，以調解插入和擷取。 標頭也會定義相關的操作工具。 此標頭檔通常會由其他 iostreams 標頭為您納入；您很少需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|型別`basic_iostream`特殊化**char**。|
|[istream](../standard-library/istream-typedefs.md#istream)|型別`basic_istream`特殊化**char**。|
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

|類別|描述|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可執行輸入和輸出的資料流類別。|
|[basic_istream](../standard-library/basic-istream-class.md)|此範本類別描述的物件可控制擷取元素和編碼的物件從資料流緩衝區類型的項目`Elem`也稱為[char_type](../standard-library/basic-ios-class.md#char_type)，其字元特性由類別`Tr`也稱為[traits_type](../standard-library/basic-ios-class.md#traits_type)。|

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
