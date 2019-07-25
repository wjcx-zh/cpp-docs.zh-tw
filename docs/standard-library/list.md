---
title: '&lt;list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
- std::<list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: 8eb497e6a4380affd0f13f41c7b55990c562b7d3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453650"
---
# <a name="ltlistgt"></a>&lt;list&gt;

定義容器範本類別 list，以及數個支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <list>
```

> [!NOTE]
> 清單 > 程式庫也會`#include <initializer_list>`使用語句。 \<

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator!=](../standard-library/list-operators.md#op_neq)|測試運算子左邊的清單物件是否不等於右邊的清單物件。|
|[operator<](../standard-library/list-operators.md#op_lt)|測試運算子左邊的清單物件是否小於右邊的清單物件。|
|[operator\<=](../standard-library/list-operators.md#op_gt_eq)|測試運算子左邊的清單物件是否小於或等於右邊的清單物件。|
|[operator==](../standard-library/list-operators.md#op_eq_eq)|測試運算子左邊的清單物件是否等於右邊的清單物件。|
|[operator>](../standard-library/list-operators.md#op_gt)|測試運算子左邊的清單物件是否大於右邊的清單物件。|
|[operator>=](../standard-library/list-operators.md#op_gt_eq)|測試運算子左邊的清單物件是否大於或等於右邊的清單物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[swap](../standard-library/list-functions.md#swap)|交換兩個清單的項目。|

### <a name="classes"></a>類別

|||
|-|-|
|[list 類別](../standard-library/list-class.md)|序列容器的範本類別，以線性排列維護其元素，並允許有效率地在序列內的任何位置進行插入與刪除。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
