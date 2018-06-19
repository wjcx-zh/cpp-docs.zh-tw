---
title: 'Cdynamicaccessor:: Setvalue |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9322394f2b72b49afe988c371858d9ee580825ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095673"
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
儲存至指定的資料行的資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `ctype`  
 [in]處理字串類型之外任何資料類型的樣板參數 (**CHAR\***， **WCHAR\***)，而這需要特殊處理。 `GetValue` 會根據您指定這裡的適當資料類型。  
  
 `pColumnName`  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 `data`  
 [in]包含資料的記憶體指標。  
  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 值為 0 參考的書籤資料行中，如果有的話。  
  
## <a name="return-value"></a>傳回值  
 如果您想要設定字串資料，使用非樣板化版本的`GetValue`。 非樣板化版本，這個方法會傳回**void\***，指向包含指定之資料行資料的緩衝區的一部分。 傳回**NULL**如果找不到資料行。  
  
 對於所有其他資料類型，它是更容易使用的樣板化版本`GetValue`。 樣板化版本會傳回**true**成功或**false**失敗。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)