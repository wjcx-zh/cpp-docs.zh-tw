---
title: '&lt;queue&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: ed1960dffa4bfe8b1ae4105f9f31943fa7a30212
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525050"
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

定義範本類別 priority_queue 和佇列以及數個支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <queue>
```

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|測試運算子左邊的佇列物件是否不等於右邊的佇列物件。|
|[operator<](../standard-library/queue-operators.md#op_lt)|測試運算子左邊的佇列物件是否小於右邊的佇列物件。|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|測試運算子左邊的佇列物件是否小於或等於右邊的佇列物件。|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|測試運算子左邊的佇列物件是否等於右邊的佇列物件。|
|[operator>](../standard-library/queue-operators.md#op_gt)|測試運算子左邊的佇列物件是否大於右邊的佇列物件。|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|測試運算子左邊的佇列物件是否大於或等於右邊的佇列物件。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[queue 類別](../standard-library/queue-class.md)|範本容器配接器類別，其提供的功能限制對項目的存取為一些基礎容器類型的前面和後面項目。|
|[priority_queue 類別](../standard-library/priority-queue-class.md)|範本容器配接器類別，其提供的功能限制對項目的存取為一些基礎容器類型的上層項目，而這一一律為最大。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
