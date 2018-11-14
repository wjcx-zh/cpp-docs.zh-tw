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
ms.openlocfilehash: eb73c77f0e2658cf750cf17ca85549a09d1cbe51
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523763"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

定義樣板類別 [basic_ostream](../standard-library/basic-ostream-class.md)，這會調解 iostream 的插入作業。 這個標頭也會定義幾個相關的操作工具。 (通常會由另一個 iostreams 標頭為您包含這個標頭。 您很少需要直接包含這個標頭。)

## <a name="syntax"></a>語法

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|建立從型別`basic_ostream`特製化的**char**並`char_traits`特製化的**char**。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|建立從型別`basic_ostream`特製化的**wchar_t**並`char_traits`特製化的**wchar_t**。|

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

|類別|描述|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|這個樣板類別所描述的物件，可控制將項目和編碼物件插入資料流緩衝區中。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
