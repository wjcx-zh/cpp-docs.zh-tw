---
title: "Cdatasource:: Getinitializationstring |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
dev_langs: C++
helpviewer_keywords: GetInitializationString method
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0cc70e9cb1c775cf9c19f7269a5305624d27210b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cdatasourcegetinitializationstring"></a>CDataSource::GetInitializationString
擷取目前已開啟的資料來源初始化字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT GetInitializationString(   
   BSTR* pInitializationString,   
   bool bIncludePassword = false    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *pInitializationString*  
 [out]初始化字串的指標。  
  
 *bIncludePassword*  
 [in]**true**如果字串包含了密碼，; 否則**false**。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 產生的初始化字串可以用來在稍後重新開啟此資料來源連接。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)