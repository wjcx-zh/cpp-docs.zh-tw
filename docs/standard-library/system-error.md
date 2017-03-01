---
title: '&lt;system_error&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<system_error>
- std::<system_error>
- <system_error>
- system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: ad53550cce165587057910e3cd4c77427fb1cd55
ms.lasthandoff: 02/24/2017

---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;
包含標頭 `<system_error>`，以定義例外狀況類別 `system_error` 及相關樣板來處理低階系統錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
#include <system_error>  
```  
  
### <a name="objects"></a>物件  
  
|||  
|-|-|  
|[generic_category](../standard-library/system-error-functions.md#generic_category)|代表泛型錯誤的分類。|  
|[system_category](../standard-library/system-error-functions.md#system_category)|代表低階系統溢位所造成的錯誤分類。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[generic_errno](../standard-library/system-error-typedefs.md#generic_errno)|類型，代表針對 `<errno.h>` 中 Posix 所定義的所有錯誤碼巨集提供符號名稱的列舉。|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|建立 `error_code` 物件。|  
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|建立 `error_condition` 物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator==](../standard-library/system-error-operators.md#operator_eq_eq)|測試運算子左邊的物件是否等於右邊的物件。|  
|[operator!=](../standard-library/system-error-operators.md#operator_neq)|測試運算子左邊的物件是否不等於右邊的物件。|  
|[operator<](../standard-library/system-error-operators.md#operator_lt_)|測試物件是否小於傳入的物件以進行比較。|  
  
### <a name="enumerations"></a>列舉  
  
|||  
|-|-|  
|[errc](../standard-library/system-error-enums.md#errc_enumeration)|提供在 `<errno.h>` 中由 Posix 所定義的所有錯誤程式碼巨集的符號名稱。|  
  
### <a name="classes-and-structs"></a>類別和結構  
  
|||  
|-|-|  
|[error_category](../standard-library/error-category-class.md)|代表物件的抽象、通用基底，以描述錯誤碼的分類。|  
|[error_code](../standard-library/error-code-class.md)|代表實作特定的低階系統錯誤。|  
|[error_condition](../standard-library/error-condition-class.md)|代表使用者定義的錯誤碼。|  
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|代表針對 [error_code 類別](../standard-library/error-code-class.md)列舉進行測試的類型述詞。|  
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|代表針對 [error_condition 類別](../standard-library/error-condition-class.md)列舉進行測試的類型述詞。|  
|[system_error](../standard-library/system-error-class.md)|代表已擲回以報告低階系統溢位之所有例外狀況的基底類別。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<system_error>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)




