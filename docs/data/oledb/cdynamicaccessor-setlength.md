---
title: 'Cdynamicaccessor:: Setlength |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
dev_langs:
- C++
helpviewer_keywords:
- SetLength method
ms.assetid: 8109ae73-04ec-4a47-be97-ba1e60080384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ae99881309188b9cfa7ec3a93a6d4afa43ba72ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090623"
---
# <a name="cdynamicaccessorsetlength"></a>CDynamicAccessor::SetLength
設定指定的資料行的長度。  
  
## <a name="syntax"></a>語法  
  
```
bool SetLength(DBORDINAL nColumn,   
   DBLENGTH nLength)throw();  

bool SetLength(const CHAR* pColumnName,   
   DBLENGTH nLength) throw();  

bool SetLength(const WCHAR* pColumnName,   
   DBLENGTH nLength) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 值為 0 參考的書籤資料行中，如果有的話。  
  
 `nLength`  
 [in]以位元組為單位的資料行的長度。  
  
 `pColumnName`  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**如果指定的資料行的長度設定成功。 否則，此函數會傳回**false**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetLength](../../data/oledb/cdynamicaccessor-getlength.md)