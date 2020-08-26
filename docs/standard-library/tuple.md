---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: b1eeba2fced21f5a38799db7fc4af259e03bc266
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841840"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

定義樣板 `tuple`，其執行個體會保留各種不同類型的物件。

## <a name="requirements"></a>規格需求

**標頭：**\<tuple>

**命名空間：** std

## <a name="members"></a>成員

### <a name="classes-and-structs"></a>類別和結構

|名稱|描述|
|-|-|
|[元組類別](../standard-library/tuple-class.md)|包裝固定長度的元素序列。|
|[tuple_element 類別](../standard-library/tuple-element-class-tuple.md)|包裝 `tuple` 元素的類型。|
|[tuple_size 類別](../standard-library/tuple-size-class-tuple.md)|包裝 `tuple` 項目計數。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||

### <a name="objects"></a>物件

|名稱|描述|
|-|-|
|[tuple_element_t](../standard-library/tuple-functions.md#tuple_element_t)||
|[tuple_size_v](../standard-library/tuple-functions.md#tuple_size_v)||

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](../standard-library/tuple-operators.md#op_eq_eq)|物件的比較 `tuple` ，等於。|
|[operator！ =](../standard-library/tuple-operators.md#op_neq)|物件的比較 `tuple` ，不等於。|
|[運算子<](../standard-library/tuple-operators.md#op_lt)|物件的比較 `tuple` （小於）。|
|[運算子<=](../standard-library/tuple-operators.md#op_lt_eq)|物件的比較 `tuple` （小於或等於）。|
|[運算子>](../standard-library/tuple-operators.md#op_gt)|物件的比較 `tuple` ，大於。|
|[運算子>=](../standard-library/tuple-operators.md#op_gt_eq)|物件的比較 `tuple` （大於或等於）。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[應用](../standard-library/tuple-functions.md#apply)|使用元組呼叫函數。|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|結構參考的元組。|
|[get](../standard-library/tuple-functions.md#get)|從 `tuple` 物件取得項目。|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|製作的速記 `tuple` 。|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|從元素值製作 `tuple`。|
|[交換](../standard-library/tuple-functions.md#swap)||
|[tie](../standard-library/tuple-functions.md#tie)|從元素參考製作 `tuple`。|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|使用類型元素的範圍來建立元組物件。|

## <a name="see-also"></a>另請參閱

[\<array>](../standard-library/array.md)
