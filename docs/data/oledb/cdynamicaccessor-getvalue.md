---
title: CDynamicAccessor::GetValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1602b784db2f6eac0984ce1fca3fb8d1276b0666
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
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
 [in]處理字串類型之外任何資料類型的樣板參數 (**CHAR\***， **WCHAR\***)，而這需要特殊處理。 `GetValue` 會根據您指定這裡的適當資料類型。  
  
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
  
## <a name="see-also"></a>請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)