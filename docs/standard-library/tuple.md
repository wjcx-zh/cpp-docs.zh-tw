---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: ce6e005990d05676fb20752b5808d32ec88dd7b3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241543"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

定義樣板 `tuple`，其執行個體會保留各種不同類型的物件。

## <a name="requirements"></a>需求

**標頭：** \<tuple>

**命名空間：** std

## <a name="members"></a>成員

### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|[tuple 類別](../standard-library/tuple-class.md)|包裝固定長度的元素序列。|
|[tuple_element 類別](../standard-library/tuple-element-class-tuple.md)|包裝 `tuple` 元素的類型。|
|[tuple_size 類別](../standard-library/tuple-size-class-tuple.md)|包裝 `tuple` 項目計數。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||

### <a name="objects"></a>物件

|||
|-|-|
|[tuple_element_t](../standard-library/tuple-functions.md#tuple_element_t)||
|[tuple_size_v](../standard-library/tuple-functions.md#tuple_size_v)||

### <a name="operators"></a>運算子

|||
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|比較`tuple`物件，等於。|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|比較`tuple`物件不相等。|
|[operator<](../standard-library/tuple-operators.md#op_lt)|比較`tuple`物件小於。|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|比較`tuple`物件小於或等於。|
|[operator>](../standard-library/tuple-operators.md#op_gt)|比較`tuple`大於物件。|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|比較`tuple`大於或相等的物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[apply](../standard-library/tuple-functions.md#apply)|呼叫使用 tuple 的函數。|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|建構 tuple 的參考。|
|[get](../standard-library/tuple-functions.md#get)|從 `tuple` 物件取得項目。|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|進行的速記`tuple`。|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|從元素值製作 `tuple`。|
|[swap](../standard-library/tuple-functions.md#swap)||
|[tie](../standard-library/tuple-functions.md#tie)|從元素參考製作 `tuple`。|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|建構 tuple 物件的型別項目範圍。|

## <a name="see-also"></a>另請參閱

[\<array>](../standard-library/array.md)<br/>
