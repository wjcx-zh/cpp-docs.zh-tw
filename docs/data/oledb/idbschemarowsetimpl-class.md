---
title: "IDBSchemaRowsetImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDBSchemaRowsetImpl
dev_langs: C++
helpviewer_keywords: IDBSchemaRowsetImpl class
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8d901b6674c19cda5a2cc9da2826c9523280b58c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl 類別
提供結構描述資料列集的實作。  
  
## <a name="syntax"></a>語法  
  
```  
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
#### <a name="parameters"></a>參數  
 `SessionClass`  
 繼承自 `IDBSchemaRowsetImpl` 的類別。 一般而言，此類別會是使用者的工作階段類別。  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)|針對結構描述資料列集檢查限制的有效性。|  
|[CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)|為範本參數所指定的物件實作 COM 物件建立者函式。|  
|[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)|指定您在特定結構描述資料列集上支援的限制。|  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)|傳回結構描述資料列集。|  
|[GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)|傳回 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)可存取的結構描述資料列集清單。|  
  
## <a name="remarks"></a>備註  
 此類別實作 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 介面和範本化的建立者函式 [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)。  
  
 OLE DB 使用結構描述資料列集，傳回提供者內部資料的相關資料。 這類資料通常稱為「中繼資料」。 根據預設，提供者必須一律支援 `DBSCHEMA_TABLES`、 **DBSCHEMA_COLUMNS**和 **DBSCHEMA_PROVIDER_TYPES**，如＜*OLE DB 程式設計人員參考*＞ 中的 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)所述。 結構描述資料列集是在結構描述對應中指定。 如需結構描述對應項目的資訊，請參閱 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)。  
  
 [ATL 物件精靈] 中的 [OLE DB 提供者精靈] 會自動為您專案中的結構描述資料列集產生程式碼 (根據預設，此精靈支援上述的必要結構描述資料列集)。當您使用 [ATL 物件精靈] 建立消費者時，此精靈會使用結構描述資料列集，將正確的資料繫結至提供者。 如果您未實作結構描述資料列集以提供正確的中繼資料，此精靈將不會繫結正確的資料。  
  
 如需如何在提供者內支援結構描述資料列集的資訊，請參閱 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。  
  
 如需結構描述資料列集的詳細資訊，請參閱 *＜OLE DB 程式設計人員參考＞* 中的 [Schema Rowsets(結構描述資料列集)](https://msdn.microsoft.com/en-us/library/ms712921.aspx)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IDBSchemaRowsetImpl 類別成員](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)