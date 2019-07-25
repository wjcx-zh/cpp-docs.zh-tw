---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 83a0ad52735f92d731dafb32ad1be5a8278776b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447175"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定義容器範本類別選擇性和數個支援的範本。

## <a name="requirements"></a>需求

**標頭:** \<選擇性 >

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
> 除了關聯式比較以外, \<選擇性的 > 運算子也支援與**nullopt**和`T`的比較。

### <a name="functions"></a>函式

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|使物件成為選擇性。|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|[hash]()||
|[選擇性類別](../standard-library/optional-class.md)|描述不一定會包含值的物件。|
|[nullopt_t 結構](../standard-library/nullopt-t-structure.md)|描述未保留值的物件。|
|[bad_optional_access 類別](../standard-library/bad-optional-access-class.md)|描述擲回為例外狀況的物件, 以報告嘗試存取不存在的值。|

### <a name="objects"></a>物件

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
