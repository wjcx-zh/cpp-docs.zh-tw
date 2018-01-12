---
title: "Igetdatasourceimpl:: Getdatasource |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs: C++
helpviewer_keywords: GetDataSource method
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 850cdd40124566fad0bc71d70e0fc2e4f1317de9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="igetdatasourceimplgetdatasource"></a>IGetDataSourceImpl::GetDataSource
建立工作階段資料來源物件上傳回介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD(GetDataSource)(   
   REFIID riid,   
   IUnknown ** ppDataSource    
);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 如果您需要存取資料來源物件中的屬性很有用。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IGetDataSourceImpl 類別](../../data/oledb/igetdatasourceimpl-class.md)