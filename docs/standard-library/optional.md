---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: f3b4896a3cb4774e46b36480dd9769fa131fc287
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957183"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定義容器範本類別 `optional` 及數個支援範本。

## <a name="requirements"></a>需求

**標頭:** \<選擇性 >

**命名空間：** std

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|測試物件是否等於另一個物件。|
|[operator!=](../standard-library/optional-operators.md#op_neq)|測試物件是否不等於另一個物件。|
|[operator<](../standard-library/optional-operators.md#op_lt)|測試左邊的物件是否小於右邊的物件。|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|測試左邊的物件是否小於或等於右邊的物件。|
|[operator>](../standard-library/optional-operators.md#op_gt)|測試左邊的物件是否大於右邊的物件。|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|測試左邊的物件是否大於或等於右邊的物件。|

> [!NOTE]
> 除了關聯式比較以外, \<選擇性的 > 運算子也支援與**nullopt**和`T`的比較。

### <a name="functions"></a>函式

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|使物件成為選擇性。|
|[swap](../standard-library/optional-functions.md#swap)|交換兩個`optional`物件的包含值。|

### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|雜湊|傳回包含物件的雜湊。|
|[選擇性類別](../standard-library/optional-class.md)|描述不一定會包含值的物件。|
|[nullopt_t 結構](../standard-library/nullopt-t-structure.md)|描述未保留值的物件。|
|[bad_optional_access 類別](../standard-library/bad-optional-access-class.md)|描述擲回為例外狀況的物件, 以報告嘗試存取不存在的值。|

### <a name="objects"></a>物件

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|`nullopt_t`用於比較的實例。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
