---
title: '&lt;ostream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs:
- C++
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf7b8bf3015879643728358258cfe4a67536b3ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
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
|[ostream](../standard-library/ostream-typedefs.md#ostream)|從根據 `char` 特製化的 `basic_ostream` 和根據 `char` 特製化的 `char_traits` 建立類型。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|從根據 `wchar_t` 特製化的 `basic_ostream` 和根據 `wchar_t` 特製化的 `char_traits` 建立類型。|

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
