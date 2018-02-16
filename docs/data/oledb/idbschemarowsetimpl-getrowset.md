---
title: IDBSchemaRowsetImpl::GetRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
dev_langs:
- C++
helpviewer_keywords:
- GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb3e1460b4eee2de030397e05d527c219acb2bb9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
傳回結構描述資料列集。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>參數  
 `pUnkOuter`  
 [in] 彙總時即為外部 **IUnknown** ；否則為 **NULL**。  
  
 `rguidSchema`  
 [in] 所要求之結構描述資料列集 GUID 的參考 (例如 `DBSCHEMA_TABLES`)。  
  
 `cRestrictions`  
 [in] 要套用至資料列集的限制計數。  
  
 `rgRestrictions`  
 [in] 代表限制的 `cRestrictions`**VARIANT**陣列。  
  
 `riid`  
 [in] 新建立之結構描述資料列集的要求 IID。  
  
 `cPropertySets`  
 [in] 要設定的屬性集數目。  
  
 `rgPropertySets`  
 [in/out] 要在新建立的結構描述資料列集上設定的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構陣列。  
  
 `ppRowset`  
 [out] 新建立之結構描述資料列集上所要求的介面指標。  
  
## <a name="remarks"></a>備註  
 此方法需要使用者具有工作階段類別中的結構描述對應。 如果 `GetRowset` 參數等於其中一個對應項目 GUID，則 `rguidSchema` 可以使用此結構描述對應資訊建立指定的資料列集物件。 如需對應項目的說明，請參閱 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) 。  
  
 請參閱[idbschemarowset:: Getrowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx) Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 類別成員](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)