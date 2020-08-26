---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: 18df18379fbee8271ba5cf851b04210f1dfddf57
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841879"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

包含標頭 \<system_error>，以定義例外狀況類別 `system_error` 及相關樣板來處理低階系統錯誤。

## <a name="requirements"></a>規格需求

**標頭：**\<system_error>

**命名空間：** std

## <a name="members"></a>成員

### <a name="objects"></a>物件

|名稱|描述|
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|代表泛型錯誤的分類。|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|代表低階系統溢位所造成的錯誤分類。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|建立 `error_code` 物件。|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|建立 `error_condition` 物件。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator = =](../standard-library/system-error-operators.md#op_eq_eq)|測試運算子左邊的物件是否等於右邊的物件。|
|[operator！ =](../standard-library/system-error-operators.md#op_neq)|測試運算子左邊的物件是否不等於右邊的物件。|
|[運算子<](../standard-library/system-error-operators.md#op_lt)|測試物件是否小於傳入的物件以進行比較。|
|[運算子<<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>列舉

|名稱|描述|
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|提供 POSIX 所定義之所有錯誤程式碼宏的符號名稱 `<errno.h>` 。|

### <a name="classes-and-structs"></a>類別和結構

|名稱|描述|
|-|-|
|[error_category](../standard-library/error-category-class.md)|表示物件的抽象、通用基底，以描述錯誤碼的分類。|
|[error_code](../standard-library/error-code-class.md)|代表實作特定的低階系統錯誤。|
|[error_condition](../standard-library/error-condition-class.md)|代表使用者定義的錯誤碼。|
|[hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|代表針對 [error_code 類別](../standard-library/error-code-class.md)列舉進行測試的類型述詞。|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|代表針對 [error_condition 類別](../standard-library/error-condition-class.md)列舉進行測試的類型述詞。|
|[system_error](../standard-library/system-error-class.md)|代表已擲回以報告低階系統溢位之所有例外狀況的基底類別。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
