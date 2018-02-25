---
title: SCHEMA_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- SCHEMA_ENTRY macro
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eed324c184036262093e266c8d246874cd2865a7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="schemaentry"></a>SCHEMA_ENTRY
關聯類別的 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp
      SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 結構描述資料列集 GUID。 請參閱[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程式設計人員參考*取得一份結構描述資料列集和其 Guid。  
  
 *rowsetClass*  
 將建立來代表結構描述資料列集類別。  
  
## <a name="remarks"></a>備註  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)接著可以查詢的對應清單的 Guid，或如果指定的 GUID，它可以建立資料列集。 結構描述資料列`IDBSchemaRowsetImpl`建立類似於標準`CRowsetImpl`-衍生類別，不過它必須提供**Execute**具有下列簽章的方法：  
  
```  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 這**Execute**函式會填入資料列集的資料。 ATL 專案精靈建立中所述[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程式設計人員參考*，三個初始每三個必要的 OLE DB 結構描述的專案中的結構描述資料列：  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA_COLUMNS**  
  
-   **DBSCHEMA_PROVIDER_TYPES**  
  
 精靈也會將三個對應的項目中的結構描述對應。 請參閱[建立 OLE DB 樣板提供者](../../data/oledb/creating-an-ole-db-provider.md)如需有關使用精靈來建立提供者。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)