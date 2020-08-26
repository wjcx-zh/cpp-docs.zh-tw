---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: f3f6c4886d22c7cd12b29950c114fbcde8905c28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845740"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

包含 `iostreams` 標準標頭 \<iomanip> 來定義數個操作工具，每個接受單一引數。

## <a name="syntax"></a>語法

```cpp
#include <iomanip>
```

## <a name="remarks"></a>備註

上述每個操作工具都會傳回未指定的類型（由呼叫 `T1` `T10` ），該類型會將 `basic_istream` \<**Elem**, **Tr**> `::` [運算子>>](../standard-library/istream-operators.md#op_gt_gt)和 `basic_ostream` \<**Elem**, **Tr**> `::` [運算子<<](../standard-library/ostream-operators.md#op_lt_lt)。

### <a name="manipulators"></a>操作工具

|名稱|描述|
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|取得貨幣金額，可選用國際格式。|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|使用指定的格式來取得時間結構的時間。|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|提供貨幣金額，可選用國際格式。|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|以時間結構和要使用的格式字串來提供時間。|
|[引用](../standard-library/iomanip-functions.md#quoted)|可使用插入和擷取運算子以方便往返字串。|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|清除指定的旗標。|
|[setbase](../standard-library/iomanip-functions.md#setbase)|設定整數的基底。|
|[setfill](../standard-library/iomanip-functions.md#setfill)|設定將用來填滿靠右對齊顯示中的空格字元。|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|設定指定的旗標。|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|設定浮點值的有效位數。|
|[setw](../standard-library/iomanip-functions.md#setw)|指定顯示欄位的寬度。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
