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
ms.openlocfilehash: 15d955aca1406183cc348395068ba042b75d7417
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846455"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定義 basic_istream 的類別樣板，以協調 iostreams 的提取，以及同時協調插入和提取的類別樣板 basic_iostream。 標頭也會定義相關的操作工具。 此標頭檔通常會由其他 iostreams 標頭為您納入；您很少需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|特製化的型別 `basic_iostream` **`char`** 。|
|[istream](../standard-library/istream-typedefs.md#istream)|特製化的型別 `basic_istream` **`char`** 。|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|針對 **wchar** 特殊化的 `basic_iostream` 類型。|
|[wistream](../standard-library/istream-typedefs.md#wistream)|針對 **wchar** 特殊化的 `basic_istream` 類型。|

### <a name="manipulators"></a>操作工具

|名稱|描述|
|-|-|
|[Ws](../standard-library/istream-functions.md#ws)|略過資料流中的空白字元。|
|[交換](../standard-library/istream-functions.md#istream_swap)|交換兩個資料流物件。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[運算子>>](../standard-library/istream-operators.md#op_gt_gt)|從資料流中擷取字元和字串。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可執行輸入和輸出的資料流類別。|
|[basic_istream](../standard-library/basic-istream-class.md)|類別樣板描述的物件可控制如何從資料流程緩衝區將專案和編碼物件解壓縮至類型為的元素 `Elem` ，也稱為 [char_type](../standard-library/basic-ios-class.md#char_type)，其字元特性是由類別 `Tr` （也稱為 [traits_type](../standard-library/basic-ios-class.md#traits_type)）所決定。|

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
