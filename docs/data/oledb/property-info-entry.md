---
title: "PROPERTY_INFO_ENTRY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROPERTY_INFO_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY 巨集"
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# PROPERTY_INFO_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示屬性集中的特定屬性。  
  
## 語法  
  
```  
  
PROPERTY_INFO_ENTRY(  
dwPropID   
)  
  
```  
  
#### 參數  
 *dwPropID*  
 \[in\] [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，可搭配屬性集 GUID 用來識別屬性。  
  
## 備註  
 此巨集會將 `DWORD` 類型的屬性值設定為 ATLDB 中定義的預設值。 若要將屬性設定為您選擇的值，請使用 [PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md)。 若要同時設定屬性的 [VARTYPE](http://msdn.microsoft.com/zh-tw/317b911b-1805-402d-a9cb-159546bc88b4) 和 [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx)，請使用 [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md)。  
  
## 範例  
 請參閱 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)