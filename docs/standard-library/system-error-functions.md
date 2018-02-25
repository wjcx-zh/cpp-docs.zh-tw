---
title: "&lt;system_error&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 78e39c11d58fddc6bc15d6c18257b43aa427b892
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函式
||||  
|-|-|-|  
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|  
|[system_category](#system_category)|  
  
##  <a name="generic_category"></a>  generic_category  
 代表泛型錯誤的分類。  
  
```
extern const error_category& generic_category();
```  
  
### <a name="remarks"></a>備註  
 `generic_category`物件是實作[error_category](../standard-library/error-category-class.md)。  
  
##  <a name="make_error_code"></a>  make_error_code  
 建立錯誤碼物件。  
  
```
error_code make_error_code(generic_errno _Errno);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`_Errno`|要儲存於錯誤碼物件中的列舉值。|  
  
### <a name="return-value"></a>傳回值  
 錯誤碼物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="make_error_condition"></a>  make_error_condition  
 建立錯誤條件物件。  
  
```
error_condition make_error_condition(generic_errno _Errno);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`_Errno`|要儲存於錯誤條件物件中的列舉值。|  
  
### <a name="return-value"></a>傳回值  
 錯誤條件物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="system_category"></a>  system_category  
 代表低階系統溢位所造成的錯誤分類。  
  
```
extern const error_category& system_category();
```  
  
### <a name="remarks"></a>備註  
 `system_category`物件是實作[error_category](../standard-library/error-category-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [<system_error>](../standard-library/system-error.md)



