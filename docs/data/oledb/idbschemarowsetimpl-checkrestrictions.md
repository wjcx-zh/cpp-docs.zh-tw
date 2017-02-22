---
title: "IDBSchemaRowsetImpl::CheckRestrictions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CheckRestrictions"
  - "IDBSchemaRowsetImpl::CheckRestrictions"
  - "IDBSchemaRowsetImpl.CheckRestrictions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckRestrictions 方法"
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBSchemaRowsetImpl::CheckRestrictions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對結構描述資料列集檢查限制的有效性。  
  
## 語法  
  
```  
  
HRESULT CheckRestrictions(  
   REFGUID   
rguidSchema  
,  
   ULONG   
cRestrictions  
,  
   const VARIANT   
rgRestrictions  
[]  
);  
  
```  
  
#### 參數  
 `rguidSchema`  
 \[in\] 所要求之結構描述資料列集 GUID 的參考 \(例如 `DBSCHEMA_TABLES`\)。  
  
 `cRestrictions`  
 \[in\] 消費者針對結構描述資料列集傳入的限制數目。  
  
 `rgRestrictions`  
 \[in\] 要設定之限制值的長度 *cRestrictions* 陣列。 如需詳細資訊，請參閱 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 中 `rgRestrictions` 參數的說明。  
  
## 備註  
 使用 `CheckRestrictions` 針對結構描述資料列集檢查限制的有效性。 它會針對 `DBSCHEMA_TABLES`、**DBSCHEMA\_COLUMNS** 和 **DBSCHEMA\_PROVIDER\_TYPES** 結構描述資料列集檢查限制。 呼叫它可判斷消費者對 **Getrowset** 的呼叫是否正確。 如果您想要支援與以上所列不同的結構描述資料列集，您應該建立自己的函式來執行這項工作。  
  
 `CheckRestrictions` 會判斷消費者是否使用提供者支援的正確限制和正確限制類型 \(例如 `VT_BSTR` 表示字串\)，來呼叫 [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)。 它也會判斷是否支援正確的限制數目。 根據預設，`CheckRestrictions` 會透過 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 呼叫，來詢問提供者有關它在指定資料列集上支援的限制。 接著，它會將來自消費者的限制與提供者支援的限制進行比較，以判斷其為成功或失敗。  
  
 如需結構描述資料列集的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 之＜OLE DB 程式設計人員參考＞中的 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl Class Members](http://msdn.microsoft.com/zh-tw/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)