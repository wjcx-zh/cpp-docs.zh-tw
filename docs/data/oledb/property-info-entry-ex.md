---
title: "PROPERTY_INFO_ENTRY_EX | Microsoft Docs"
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
  - "PROPERTY_INFO_ENTRY_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY_EX 巨集"
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表屬性集中的特定屬性。  
  
## 語法  
  
```  
  
PROPERTY_INFO_ENTRY_EX(  
dwPropID  
,  
vt  
,  
dwFlags  
,  
value  
,  
options  
)  
  
```  
  
#### 參數  
 *dwPropID*  
 \[in\] [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) 值，可搭配屬性集 GUID 以識別屬性。  
  
 *vt*  
 \[in\] 此屬性項目的 [VARTYPE](http://msdn.microsoft.com/zh-tw/317b911b-1805-402d-a9cb-159546bc88b4)。  
  
 `dwFlags`  
 \[in\] 描述此屬性項目的 [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) 值。  
  
 *值*  
 \[in\] `DWORD` 類型的屬性值。  
  
 `options`  
 **DBPROPOPTIONS\_REQUIRED** 或 **DBPROPOPTIONS\_SETIFCHEAP**。 一般而言，提供者不需要設定 `options`，因為它是由消費者所設定。  
  
## 備註  
 透過這個巨集，您可以直接指定 `DWORD` 類型的屬性值，以及選項和旗標。 若只要將屬性設定為 ATLDB.H 中定義的預設值，請使用 [PROPERTY\_INFO\_ENTRY](../../data/oledb/property-info-entry.md)。 若要將屬性設定為您選擇的值，請使用 [PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md)，而不需要設定屬性的選項或旗標。  
  
## 範例  
 請參閱 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)