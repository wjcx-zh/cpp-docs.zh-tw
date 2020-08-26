---
title: '&lt;選用&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: 31a3d9aad539e45bb835331a4ef63690d0e16f49
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842672"
---
# <a name="ltoptionalgt"></a>&lt;選用&gt;

定義容器類別範本 `optional` 和數個支援的範本。

## <a name="requirements"></a>規格需求

**標頭：**\<optional>

**命名空間：** std

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](../standard-library/optional-operators.md#op_eq_eq)|測試物件是否等於另一個物件。|
|[operator！ =](../standard-library/optional-operators.md#op_neq)|測試物件是否不等於另一個物件。|
|[運算子<](../standard-library/optional-operators.md#op_lt)|測試左邊的物件是否小於右邊的物件。|
|[運算子<=](../standard-library/optional-operators.md#op_lt_eq)|測試左邊的物件是否小於或等於右邊的物件。|
|[運算子>](../standard-library/optional-operators.md#op_gt)|測試左邊的物件是否大於右邊的物件。|
|[運算子>=](../standard-library/optional-operators.md#op_lt_eq)|測試左邊的物件是否大於或等於右邊的物件。|

> [!NOTE]
> 除了關聯式比較， \<optional> 運算子也支援與 **nullopt** 和的比較 `T` 。

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|讓物件成為選擇性的。|
|[交換](../standard-library/optional-functions.md#swap)|交換兩個物件的包含值 `optional` 。|

### <a name="classes-and-structs"></a>類別和結構

|名稱|描述|
|-|-|
|雜湊|傳回包含物件的雜湊。|
|[選擇性類別](../standard-library/optional-class.md)|描述可能或可能不會保留值的物件。|
|[nullopt_t 結構](../standard-library/nullopt-t-structure.md)|描述未保留值的物件。|
|[bad_optional_access 類別](../standard-library/bad-optional-access-class.md)|描述擲回做為例外狀況的物件，以報告嘗試存取不存在的值。|

### <a name="objects"></a>物件

|名稱|描述|
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|`nullopt_t`用於比較的實例。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
