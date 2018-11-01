---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: 2e46b3997096c6e61f7dd6140131e3f10223b8e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586663"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

定義樣板 `tuple`，其執行個體會保留各種不同類型的物件。

## <a name="syntax"></a>語法

```cpp
#include <tuple>
```

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[tuple](../standard-library/tuple-class.md)|包裝固定長度的元素序列。|
|[tuple_element 類別](../standard-library/tuple-element-class-tuple.md)|包裝 `tuple` 元素的類型。|
|[tuple_size 類別](../standard-library/tuple-size-class-tuple.md)|包裝 `tuple` 項目計數。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|比較 `tuple` 物件 (等於)|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|比較 `tuple` 物件 (不等於)|
|[operator<](../standard-library/tuple-operators.md#op_lt)|比較 `tuple` 物件 (小於)|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|比較 `tuple` 物件 (小於或等於)|
|[operator>](../standard-library/tuple-operators.md#op_gt)|比較 `tuple` 物件 (大於)|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|比較 `tuple` 物件 (大於或等於)|

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[get](../standard-library/tuple-functions.md#get)|從 `tuple` 物件取得項目。|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|從元素值製作 `tuple`。|
|[tie](../standard-library/tuple-functions.md#tie)|從元素參考製作 `tuple`。|

## <a name="see-also"></a>另請參閱

[\<array>](../standard-library/array.md)<br/>
