---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: ffcb6c7b2f95b0b62659f6080c9ed0d1f111237c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846390"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

定義 [basic_ostream](../standard-library/basic-ostream-class.md)的類別範本，以協調 iostreams 的插入。 這個標頭也會定義幾個相關的操作工具。 (通常會由另一個 iostreams 標頭為您包含這個標頭。 您很少需要直接包含這個標頭。)

## <a name="syntax"></a>語法

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|從建立型別， `basic_ostream` **`char`** 並 `char_traits` 在上特製化 **`char`** 。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|從建立型別， `basic_ostream` **`wchar_t`** 並 `char_traits` 在上特製化 **`wchar_t`** 。|

### <a name="manipulators"></a>操作工具

|名稱|描述|
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|結束一行並清除緩衝區。|
|[結束](../standard-library/ostream-functions.md#ends)|結束字串。|
|[沖洗](../standard-library/ostream-functions.md#flush)|清除緩衝區。|
|[交換](../standard-library/ostream-functions.md#swap)|將左 `basic_ostream` 物件參數的值與右 `basic_ostream` 物件參數的值交換。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[運算子<<](../standard-library/ostream-operators.md#op_lt_lt)|將各種類型寫入資料流。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|類別樣板描述的物件可控制如何將元素和編碼物件插入資料流程緩衝區中。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
