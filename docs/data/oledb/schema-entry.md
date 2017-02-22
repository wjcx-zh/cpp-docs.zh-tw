---
title: "SCHEMA_ENTRY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SCHEMA_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SCHEMA_ENTRY 巨集"
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SCHEMA_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

相關聯的 GUID 和類別。  
  
## 語法  
  
```  
  
      SCHEMA_ENTRY(  
   guid,  
   rowsetClass   
);   
```  
  
#### 參數  
 `guid`  
 結構描述資料列集 GUID。  指定結構描述資料列集和它們的 GUID 清單。請參閱《 *OLE DB 程式設計人員參考》的*[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 。  
  
 *rowsetClass*  
 會建立表示結構描述資料列集的類別。  
  
## 備註  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 可以查詢 GUID 清單的對應，也可以建立資料列集，如果將 GUID。  結構描述資料列集 `IDBSchemaRowsetImpl` 建立類似於標準 `CRowsetImpl`衍生類別，不過，它必須提供具有下列簽章的 **Execute** 方法:  
  
 `HRESULT Execute (LONG* pcRowsAffected, ULONG cRestrictions,`  
  
 `const VARIANT* rgRestrictions)`  
  
 這個函式 **Execute** 填入資料列集的資料。  ATL 專案精靈建立，如《 *OLE DB 程式設計人員參考》的*[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 所述，三個初始結構描述資料列集在三個必須的 OLE DB 結構描述中的每一個專案:  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA\_COLUMNS**  
  
-   **DBSCHEMA\_PROVIDER\_TYPES**  
  
 精靈也會將結構描述對應的三個對應的項目。  請參閱 [建立 OLE DB 提供者樣板](../../data/oledb/creating-an-ole-db-provider.md) 。如需使用精靈的詳細資訊建立提供者。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN\_SCHEMA\_MAP](../../data/oledb/begin-schema-map.md)   
 [END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)