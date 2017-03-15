---
title: "PROPERTY_INFO_ENTRY_VALUE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROPERTY_INFO_ENTRY_VALUE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY_VALUE 巨集"
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY_VALUE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示屬性集合中的特定屬性。  
  
## 語法  
  
```  
  
PROPERTY_INFO_ENTRY_VALUE(  
dwPropID  
, value )  
```  
  
#### 參數  
 *dwPropID*  
 \[in\] 可以和屬性集 GUID 一起用來識別屬性的 [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值。  
  
 *value*  
 \[in\] 型別為 `DWORD` 的屬性值。  
  
## 備註  
 這個巨集，可以直接指定屬性值型別 `DWORD`。  僅設定屬性至 ATLDB.H 定義的預設值，請使用 [PROPERTY\_INFO\_ENTRY](../../data/oledb/property-info-entry.md)。  要設定其值，旗標和選項屬性的，請使用 [PROPERTY\_INFO\_ENTRY\_EX 巨集。](../../data/oledb/property-info-entry-ex.md)。  
  
## 範例  
 請參閱 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)