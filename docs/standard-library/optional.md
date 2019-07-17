---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: c73ad2ad94a5de29bc2c457fdf6ca8b9c783615c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268480"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定義容器範本類別的選擇性和幾個支援範本。

## <a name="requirements"></a>需求

**標頭：** \<選擇性 >

**命名空間：** std

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|測試運算子左邊的 `optional` 物件是否等於右邊的 `optional` 物件。|
|[operator!=](../standard-library/optional-operators.md#op_neq)|測試運算子左邊的 `optional` 物件是否不等於右邊的 `optional` 物件。|
|[operator<](../standard-library/optional-operators.md#op_lt)|測試運算子左邊的 `optional` 物件是否小於右邊的 `optional` 物件。|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|測試運算子左邊的 `optional` 物件是否小於或等於右邊的 `optional` 物件。|
|[operator>](../standard-library/optional-operators.md#op_gt)|測試運算子左邊的 `optional` 物件是否大於右邊的 `optional` 物件。|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|測試運算子左邊的 `optional` 物件是否大於或等於右邊的 `optional` 物件。|

> [!NOTE]
> 除了關聯式的比較\<選擇性 > 運算子也支援與比較**nullopt**和`T`。

### <a name="functions"></a>函式

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|提供物件的選項。|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|[hash]()||
|[可省略的類別](../standard-library/optional-class.md)|描述的物件，可能會或可能不會保存的值。|
|[nullopt_t 結構](../standard-library/nullopt-t-structure.md)|描述不保留值的物件。|
|[bad_optional_access 類別](../standard-library/bad-optional-access-class.md)|描述擲回例外狀況報告嘗試存取的值不存在的物件。|

### <a name="objects"></a>物件

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
