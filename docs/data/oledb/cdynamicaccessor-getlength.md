---
title: "Cdynamicaccessor:: Getlength |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
dev_langs: C++
helpviewer_keywords: GetLength method
ms.assetid: 3ae8983b-b267-4cf9-bfc0-3e191f79e646
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 24a22348b873967a860c65edb5c4f6d46ab101ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorgetlength"></a>CDynamicAccessor::GetLength
擷取指定之資料行的長度。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool GetLength(   
   DBORDINAL nColumn,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const CHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const WCHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `nColumn`  
 [in] 資料行編號。 資料行數字開頭為 1。 值為 0 參考的書籤資料行中，如果有的話。  
  
 `pColumnName`  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 `pLength`  
 [out]包含以位元組為單位的資料行長度的整數指標。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**如果找到指定的資料行。 否則，此函數會傳回**false**。  
  
## <a name="remarks"></a>備註  
 第一個覆寫會採用資料行數目，而第二個和第三個覆寫需要資料行名稱 ANSI 或 Unicode 格式，分別。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetLength](../../data/oledb/cdynamicaccessor-setlength.md)