---
title: "IDBSchemaRowsetImpl::SetRestrictions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBSchemaRowsetImpl::SetRestrictions"
  - "SetRestrictions"
  - "IDBSchemaRowsetImpl.SetRestrictions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetRestrictions 方法"
ms.assetid: 707d5065-b853-4d38-9b67-3066b4d3b279
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IDBSchemaRowsetImpl::SetRestrictions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定您在特定結構描述資料列集上支援的限制。  
  
## 語法  
  
```  
  
void SetRestrictions(  
   ULONG   
cRestrictions  
,  
   GUID* /*   
rguidSchema  
*/,  
   ULONG*   
rgRestrictions  
);  
  
```  
  
#### 參數  
 `cRestrictions`  
 \[in\] `rgRestrictions` 陣列中的限制數目，以及 `rguidSchema` 陣列中的 GUID 數目。  
  
 `rguidSchema`  
 \[in\] 要擷取限制之目標結構描述資料列集的 GUID 陣列。 每個陣列元素包含一個結構描述資料列集的 GUID \(例如 `DBSCHEMA_TABLES`\)。  
  
 `rgRestrictions`  
 \[in\] 要設定之限制值的長度 `cRestrictions` 陣列。 每個元素會對應至 GUID 所識別之結構描述資料列集上的限制。 如果提供者不支援結構描述資料列集，此元素會設定為零。 否則，**ULONG** 值會包含代表該結構描述資料列集支援之限制的位元遮罩。 如需對應至特定結構描述資料列集之限制的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 之＜OLE DB 程式設計人員參考＞中的 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
## 備註  
 **IDBSchemaRowset** 物件會呼叫 `SetRestrictions`，來判斷您在特定結構描述資料列集上支援的限制 \(它是由 [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) 透過向上轉型的指標進行呼叫\)。 限制允許消費者只擷取相符的資料列 \(例如在資料表 "MyTable" 中尋找所有資料行\)。 限制是選擇性的，在不支援任何限制的情況下 \(預設\)，一律會傳回所有資料。  
  
 此方法的預設實作會將 `rgRestrictions` 陣列元素設定為 0。 您可以覆寫工作階段類別中的預設，將限制設定為非預設。  
  
 如需實作結構描述資料列集支援的資訊，請參閱[支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。  
  
 如需支援結構描述資料列集的提供者範例，請參閱 [UpdatePV](../../top/visual-cpp-samples.md) 範例。  
  
 如需結構描述資料列集的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 之＜OLE DB 程式設計人員參考＞中的 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IDBSchemaRowsetImpl 類別](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl Class Members](http://msdn.microsoft.com/zh-tw/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)   
 [UpdatePV](../../top/visual-cpp-samples.md)