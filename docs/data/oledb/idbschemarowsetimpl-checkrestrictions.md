---
title: "Idbschemarowsetimpl:: Checkrestrictions |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
dev_langs: C++
helpviewer_keywords: CheckRestrictions method
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ee1da1c01fcaa1670449248f3f8208b2a915783
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="idbschemarowsetimplcheckrestrictions"></a>IDBSchemaRowsetImpl::CheckRestrictions
針對結構描述資料列集檢查限制的有效性。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT CheckRestrictions(  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rguidSchema`  
 [in] 所要求之結構描述資料列集 GUID 的參考 (例如 `DBSCHEMA_TABLES`)。  
  
 `cRestrictions`  
 [in] 消費者針對結構描述資料列集傳入的限制數目。  
  
 `rgRestrictions`  
 [in] 要設定之限制值的長度 *cRestrictions* 陣列。 如需詳細資訊，請參閱 `rgRestrictions` SetRestrictions [中](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)參數的說明。  
  
## <a name="remarks"></a>備註  
 使用 `CheckRestrictions` 針對結構描述資料列集檢查限制的有效性。 它會針對 `DBSCHEMA_TABLES`、 **DBSCHEMA_COLUMNS**和 **DBSCHEMA_PROVIDER_TYPES** 結構描述資料列集檢查限制。 呼叫它可判斷消費者對 **Getrowset** 的呼叫是否正確。 如果您想要支援與以上所列不同的結構描述資料列集，您應該建立自己的函式來執行這項工作。  
  
 `CheckRestrictions` 會判斷消費者是否使用提供者支援的正確限制和正確限制類型 (例如 [表示字串)，來呼叫](../../data/oledb/idbschemarowsetimpl-getrowset.md) GetRowset `VT_BSTR` 。 它也會判斷是否支援正確的限制數目。 根據預設， `CheckRestrictions` 會透過 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 呼叫，來詢問提供者有關它在指定資料列集上支援的限制。 接著，它會將來自消費者的限制與提供者支援的限制進行比較，以判斷其為成功或失敗。  
  
 如需有關結構描述資料列集的詳細資訊，請參閱[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl 類別成員](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)