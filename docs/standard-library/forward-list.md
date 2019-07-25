---
title: '&lt;forward_list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <forward_list>
helpviewer_keywords:
- <forward_list>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: a8b343fbe5e175828b4b8470da486a6dea9f3455
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457005"
---
# <a name="ltforwardlistgt"></a>&lt;forward_list&gt;

定義容器範本類別 forward_list，以及數個支援的範本。

## <a name="requirements"></a>需求

**標頭：** \<forward_list>

**命名空間：** std

> [!NOTE]
> Forward_list > 程式庫也會`#include <initializer_list>`使用語句。 \<

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|測試運算子左邊的轉送清單物件是否等於右邊的轉送清單物件。|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|測試運算子左邊的轉送清單物件是否不等於右邊的轉送清單物件。|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|測試運算子左邊的轉送清單物件是否小於右邊的轉送清單物件。|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的轉送清單物件是否小於或等於右邊的轉送清單物件。|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|測試運算子左邊的轉送清單物件是否大於右邊的轉送清單物件。|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的轉送清單物件是否大於或等於右邊的轉送清單物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[swap](../standard-library/forward-list-functions.md#swap)|交換兩個轉送清單的項目。|

### <a name="classes"></a>類別

|||
|-|-|
|[forward_list](../standard-library/forward-list-class.md)|描述一個控制不同長度項目序列的物件。 這個序列會以元素的單向連結清單形式儲存，每個元素都包含一個 `Type` 類型的成員。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
