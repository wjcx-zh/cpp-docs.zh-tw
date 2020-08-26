---
title: '&lt;variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 1a3c861c96fedb7ef95eec66f95888ddc092bed4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835658"
---
# <a name="ltvariantgt"></a>&lt;variant&gt;

Variant 物件會保存及管理值。 如果變數保留值，該值的型別必須是提供給 variant 的其中一個樣板引數類型。 這些範本引數稱為替代專案。

## <a name="requirements"></a>規格需求

**標頭：**\<variant>

**命名空間：** std

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](../standard-library/forward-list-operators.md#op_eq_eq)|測試運算子左邊的 variant 物件是否相等於右邊的 variant 物件。|
|[operator！ =](../standard-library/forward-list-operators.md#op_neq)|測試運算子左邊的 variant 物件是否不等於右邊的 variant 物件。。|
|[運算子<](../standard-library/forward-list-operators.md#op_lt)|測試運算子左邊的 variant 物件是否小於右邊的變異數物件。|
|[運算子<=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的 variant 物件，是否小於或等於右邊的 variant 物件（variant object）。|
|[運算子>](../standard-library/forward-list-operators.md#op_gt)|測試運算子左邊的 variant 物件是否大於右邊的 variant 物件。。|
|[運算子>=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的 variant 物件是否大於或等於右邊的 variant 物件。（）|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[get](../standard-library/variant-functions.md#get)|取得物件的變體。|
|[get_if](../standard-library/variant-functions.md#get_if)|取得物件的變異（如果存在的話）。|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|**`true`** 如果變數存在，則傳回。|
|[交換](../standard-library/variant-functions.md#swap)|交換 **變異**數。|
|[訪問](../standard-library/variant-functions.md#visit)|移至下一個 **變異**。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|擲回的物件會向 variant 物件的值報告不正確存取權。|
|[variant](../standard-library/variant.md)|要保留其中一個替代類型值的物件，或沒有值的物件。|

### <a name="structs"></a>結構

|名稱|描述|
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|Variant 的替代類型，讓 variant 類型成為預設可建構。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|協助 variant 物件。|
|[variant_size](../standard-library/variant-size-structure.md)|協助 variant 物件。|

### <a name="objects"></a>物件

|名稱|描述|
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
