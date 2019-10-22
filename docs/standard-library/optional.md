---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: bce31811c98d351f3c561b3136d41f7ed23d13e0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687250"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定義容器類別範本 `optional` 和數個支援的範本。

## <a name="requirements"></a>需求

**標頭：** \<optional >

**命名空間:** std

## <a name="members"></a>Members

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
> 除了關聯式比較以外，\<optional > 運算子也支援與**nullopt**和 `T` 的比較。

### <a name="functions"></a>函式

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|使物件成為選擇性。|
|[swap](../standard-library/optional-functions.md#swap)|交換兩個 `optional` 物件的包含值。|

### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|雜湊|傳回包含物件的雜湊。|
|[選擇性類別](../standard-library/optional-class.md)|描述不一定會包含值的物件。|
|[nullopt_t 結構](../standard-library/nullopt-t-structure.md)|描述未保留值的物件。|
|[bad_optional_access 類別](../standard-library/bad-optional-access-class.md)|描述擲回為例外狀況的物件，以報告嘗試存取不存在的值。|

### <a name="objects"></a>物件

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|用於比較的 `nullopt_t` 實例。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
