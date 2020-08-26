---
title: '&lt;array&gt;'
ms.date: 11/04/2016
f1_keywords:
- <array>
helpviewer_keywords:
- array header
ms.assetid: 084147c1-e805-478e-8201-76846020f187
ms.openlocfilehash: b515578e658d658722f92e48a7ac5ab78727c465
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834943"
---
# <a name="ltarraygt"></a>&lt;array&gt;

定義容器類別範本 **陣列** 和數個支援的範本。

## <a name="requirements"></a>規格需求

**標頭：**\<array>

**命名空間：** std

> [!NOTE]
> 連結 \<array> 庫也會使用 `#include <initializer_list>` 語句。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[array](../standard-library/array-class-stl.md)|儲存固定長度的元素序列。|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|包裝陣列元素的類型。|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|包裝陣列元素的大小。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](../standard-library/array-operators.md#op_eq_eq)|陣列比較，相等|
|[operator！ =](../standard-library/array-operators.md#op_neq)|陣列比較，不相等|
|[運算元\<](../standard-library/array-operators.md#op_lt)|陣列比較，小於|
|[運算子>=](../standard-library/array-operators.md#op_gt_eq)|陣列比較，大於或相等|
|[運算子>](../standard-library/array-operators.md#op_gt)|陣列比較，大於|
|[運算子<=](../standard-library/array-operators.md#op_lt_eq)|陣列比較，小於或相等|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[get](../standard-library/array-functions.md#get)|取得指定的陣列元素。|
|[交換](../standard-library/array-functions.md#swap)|交換其中一個陣列的內容與另一個陣列的內容。|

## <a name="see-also"></a>另請參閱

[\<tuple>](../standard-library/tuple.md)\
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
