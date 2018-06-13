---
title: 'Cdynamicaccessor:: Getvalue |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- GetValue method
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e43707d4697fbbeece5475f71b7e2f93e731772
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096414"
---
# <a name="cdynamicaccessorgetvalue"></a>CDynamicAccessor::GetValue
擷取指定之資料行的資料。  
  
## <a name="syntax"></a>語法  
  
```cpp
void* GetValue(DBORDINAL nColumn) const throw();  

void* GetValue(const CHAR* pColumnName) const throw();  

void* GetValue(const WCHAR* pColumnName) const throw();  

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `ctype`  
 if the column is not found[in]處理字串類型之外任何資料類型的樣板參數 (**CHAR\***， **WCHAR\***)，而這需要特殊處理。 `GetValue` 會根據您指定這裡的適當資料類型。  
  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 值為 0 參考的書籤資料行中，如果有的話。  
  
 `pColumnName`  
 [in]資料行名稱。  
  
 `pData`  
 [out]指定資料行的內容指標。  
  
## <a name="return-value"></a>傳回值  
 如果您想要傳遞的字串資料，使用非樣板化版本的`GetValue`。 非樣板化版本，這個方法會傳回**void\***，指向包含指定之資料行資料的緩衝區的一部分。 傳回**NULL**如果找不到資料行。  
  
 對於所有其他資料類型，它是更容易使用的樣板化版本`GetValue`。 樣板化版本會傳回**true**成功或**false**失敗。  
  
## <a name="remarks"></a>備註  
 傳回包含字串和資料行包含其他資料類型的樣板化版本的資料行使用非樣板化版本。  
  
 在偵錯模式中，就會判斷提示，如果大小`pData`是它所指向的資料行的大小不相等。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)