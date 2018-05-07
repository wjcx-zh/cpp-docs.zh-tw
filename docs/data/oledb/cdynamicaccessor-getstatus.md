---
title: 'Cdynamicaccessor:: Getstatus |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: 8f1aba69-5c2c-4ca7-ad84-7b4b27995eb8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 98e120e19c6115b98ed57bc8d25a934b84573386
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetstatus"></a>CDynamicAccessor::GetStatus
擷取指定之資料行的狀態。  
  
## <a name="syntax"></a>語法  
  
```
bool GetStatus(DBORDINAL nColumn,   
  DBSTATUS* pStatus) const throw();  

bool GetStatus(const CHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const WCHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 值為 0 參考的書籤資料行中，如果有的話。  
  
 `pColumnName`  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 `pStatus`  
 [out]包含資料行狀態變數的指標。 請參閱[DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**如果找到指定的資料行。 否則，此函數會傳回**false**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)