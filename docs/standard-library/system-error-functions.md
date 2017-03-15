---
title: "&lt;system_error&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 43098f6f9276c9a66aaa7a30c95a6696e33f8429
ms.lasthandoff: 02/24/2017

---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函式
||||  
|-|-|-|  
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|  
|[system_category](#system_category)|  
  
##  <a name="a-namegenericcategorya--genericcategory"></a><a name="generic_category"></a>  generic_category  
 代表泛型錯誤的分類。  
  
```
extern const error_category& generic_category();
```  
  
### <a name="remarks"></a>備註  
 `generic_categor`y 物件是 [error_category](../standard-library/error-category-class.md) 的實作。  
  
##  <a name="a-namemakeerrorcodea--makeerrorcode"></a><a name="make_error_code"></a>  make_error_code  
 建立錯誤碼物件。  
  
```
error_code make_error_code(generic_errno _Errno);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`_Errno`|要儲存於錯誤碼物件中的列舉值。|  
  
### <a name="return-value"></a>傳回值  
 錯誤碼物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemakeerrorconditiona--makeerrorcondition"></a><a name="make_error_condition"></a>  make_error_condition  
 建立錯誤條件物件。  
  
```
error_condition make_error_condition(generic_errno _Errno);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`_Errno`|要儲存於錯誤條件物件中的列舉值。|  
  
### <a name="return-value"></a>傳回值  
 錯誤條件物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesystemcategorya--systemcategory"></a><a name="system_category"></a>  system_category  
 代表低階系統溢位所造成的錯誤分類。  
  
```
extern const error_category& system_category();
```  
  
### <a name="remarks"></a>備註  
 `system_categor`y 物件是 [error_category](../standard-library/error-category-class.md) 的實作。  
  
## <a name="see-also"></a>另請參閱  
 [<system_error>](../standard-library/system-error.md)




