---
title: "Cdynamicaccessor:: Getordinal |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
dev_langs: C++
helpviewer_keywords: GetOrdinal method
ms.assetid: 2095b71c-a7a4-4034-89a1-77a78cb9633f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6ea8e4e4478b47a333facfbb38bfeb856ef08fe3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetordinal"></a>CDynamicAccessor::GetOrdinal
擷取指定資料行名稱的資料行數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool GetOrdinal(  
   const CHAR* pColumnName,  
   DBORDINAL* pOrdinal   
) const throw( );  
bool GetOrdinal(  
   const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal   
) const throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `pColumnName`  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 *pOrdinal*  
 [out] 指向資料行數目的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**如果找到具有指定名稱的資料行。 否則，此函數會傳回**false**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)