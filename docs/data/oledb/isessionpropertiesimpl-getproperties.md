---
title: "Isessionpropertiesimpl:: Getproperties |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
dev_langs: C++
helpviewer_keywords: GetProperties method
ms.assetid: 48726c2a-9599-4fc5-9940-a932faef91ab
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5fa22fb3045bb8ec96c21cd8e92288989bbab798
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="isessionpropertiesimplgetproperties"></a>ISessionPropertiesImpl::GetProperties
傳回清單中的屬性**DBPROPSET_SESSION**目前所設定的工作階段的屬性群組。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets    
);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[ISessionProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms723643.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [ISessionPropertiesImpl 類別](../../data/oledb/isessionpropertiesimpl-class.md)   
 [ISessionPropertiesImpl::SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)