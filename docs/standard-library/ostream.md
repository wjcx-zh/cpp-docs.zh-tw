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
ms.openlocfilehash: 3838e215ffac42ec6902ab6a9837f638153cf184
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689158"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

定義類別樣板[basic_ostream](../standard-library/basic-ostream-class.md)，以調節 iostreams 的插入。 這個標頭也會定義幾個相關的操作工具。 (通常會由另一個 iostreams 標頭為您包含這個標頭。 您很少需要直接包含這個標頭。)

## <a name="syntax"></a>語法

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|根據 char 上特製化的 `basic_ostream` 建立型別 **，並 `char_traits`** 在**char**上特製化。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|根據 wchar_t 上特製化的 `basic_ostream` 建立型別 **，並 `char_traits`** 在**wchar_t**上特製化。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|結束一行並清除緩衝區。|
|[ends](../standard-library/ostream-functions.md#ends)|結束字串。|
|[flush](../standard-library/ostream-functions.md#flush)|清除緩衝區。|
|[swap](../standard-library/ostream-functions.md#swap)|將左 `basic_ostream` 物件參數的值與右 `basic_ostream` 物件參數的值交換。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|將各種類型寫入資料流。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|類別樣板描述一個物件，可控制將專案和編碼物件插入資料流程緩衝區。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
