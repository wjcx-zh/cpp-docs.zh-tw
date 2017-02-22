---
title: "PROVIDER_COLUMN_ENTRY_GN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_COLUMN_ENTRY_GN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROVIDER_COLUMN_ENTRY_GN 巨集"
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# PROVIDER_COLUMN_ENTRY_GN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示提供者支援的特定資料行。  
  
## 語法  
  
```  
  
PROVIDER_COLUMN_ENTRY_GN (  
name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### 參數  
 *name*  
 \[資料行名稱。  
  
 `ordinal`  
 \[的資料列數目。  除非資料行是書籤資料行，不能為 0。  
  
 `flags`  
 \[\] 指定資料的方式傳回。  請參閱在 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 `dwFlags` 描述。  
  
 *colSize*  
 \[資料行大小。  
  
 `dbtype`  
 \[表示值的資料型別。  請參閱 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中的 **wType** 描述。  
  
 *precision*  
 \[時表示精確度使用取得資料，則為 `DBTYPE_NUMERIC`*dbType* 或 **DBTYPE\_DECIMAL**。  請參閱 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中的 **bPrecision** 描述。  
  
 `scale`  
 \[時表示縮放使用取得資料，則為 `DBTYPE_NUMERIC` dbType 或 **DBTYPE\_DECIMAL**。  請參閱 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中的 **bScale** 描述。  
  
 `guid`  
 結構描述資料列集 GUID。  指定結構描述資料列集和它們的 GUID 清單。請參閱《 *OLE DB 程式設計人員參考》的*[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 。  
  
## 備註  
 可讓您指定資料行的大小、資料型別、精確度、小數點位數和結構描述資料列集 GUID。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)