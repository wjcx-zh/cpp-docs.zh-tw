---
title: "Idbschemarowsetimpl:: Getschemas |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs: C++
helpviewer_keywords: GetSchemas method
ms.assetid: fbe725a6-3acd-45f8-bcaf-10a6c1239cd2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 20d346ff4b2ed3dd3f4fc90190c51e1fa41dbc46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="idbschemarowsetimplgetschemas"></a>IDBSchemaRowsetImpl::GetSchemas
傳回 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)可存取的結構描述資料列集清單。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD ( GetSchema s )(  
   ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest  
);  
```  
  
#### <a name="parameters"></a>參數  
 *pcSchemas*  
 [out] 要填入結構描述數目的 **ULONG** 指標。  
  
 *prgSchemas*  
 [out] 要填入結構描述資料列集 GUID 陣列指標的 GUID 陣列指標。  
  
 *prgRest*  
 [out] 要填入限制陣列的 **ULONG**陣列指標。  
  
## <a name="remarks"></a>備註  
 此方法會傳回提供者支援之所有結構描述資料列集的陣列。 請參閱[idbschemarowset:: Getschemas](https://msdn.microsoft.com/en-us/library/ms719605.aspx) Windows SDK 中。  
  
 此函式的實作需要使用者具有工作階段類別中的結構描述對應。 藉由使用此結構描述對應資訊，它就能接著以對應中結構描述的 GUID 陣列來回應。 這會是提供者支援的結構描述。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 類別成員](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Idbschemarowsetimpl:: Getrowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)   
 [Idbschemarowset:: Getrowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)