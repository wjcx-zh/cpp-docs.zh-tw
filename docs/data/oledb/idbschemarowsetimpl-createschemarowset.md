---
title: 'Idbschemarowsetimpl:: Createschemarowset |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateSchemaRowset method
ms.assetid: ad3e3e4d-45b9-461c-b7b8-3af6843631b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 90a942fc92faf3066669b46fd825ad2eae393f43
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="idbschemarowsetimplcreateschemarowset"></a>IDBSchemaRowsetImpl::CreateSchemaRowset
為範本參數所指定的物件實作 COM 物件建立者函式。  
  
## <a name="syntax"></a>語法  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>參數  
 `pUnkOuter`  
 [in] 彙總時即為外部 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) ；否則為 **NULL**。  
  
 `cRestrictions`  
 [in] 套用至結構描述資料列集的限制計數。  
  
 `rgRestrictions`  
 [in] 要套用至資料列集的 `cRestrictions`**VARIANT**陣列。  
  
 `riid`  
 [in] 輸出 [IUnknown](../../atl/queryinterface.md) 時的 **QueryInterface**介面  
  
 `cPropertySets`  
 [in] 要設定的屬性集數目。  
  
 `rgPropertySets`  
 [in] 指定要設定之屬性的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構陣列。  
  
 `ppRowset`  
 [out] **要求的傳出** IUnknown `riid`。 此 **IUnknown** 是結構描述資料列集物件上的介面。  
  
 `pSchemaRowset`  
 [out] 結構描述資料列集類別執行個體的指標。 一般而言，您不會使用此參數；但如果您必須對結構描述資料列集執行更多工作，才能送出至 COM 物件，則可以使用此參數。 `pSchemaRowset` 的存留期受限於 `ppRowset`。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
## <a name="remarks"></a>備註  
 此函式會對所有類型的結構描述資料列集實作一般建立者。 一般而言，使用者不會呼叫此函式， 而是由結構描述對應的實作進行呼叫。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 類別成員](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)