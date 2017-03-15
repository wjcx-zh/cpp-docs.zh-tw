---
title: "CUtlProps 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CUtlProps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUtlProps 類別"
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CUtlProps 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作各種 OLE DB 屬性介面的屬性 \(例如， `IDBProperties`、 `IDBProperties`和 `IRowsetInfo`\)。  
  
## 語法  
  
```  
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### 參數  
 `T`  
 包含 `BEGIN_PROPSET_MAP`的類別。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|從屬性集合取得屬性。|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|用來在設定屬性之前先驗證值。|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|當消費者呼叫在建立物件時，介面的方法處理要求選擇性介面。|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|會在設定屬性之後的繫結屬性。|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|設定屬性集合的屬性。|  
  
## 備註  
 這個類別的大部分是實作詳細資料。  
  
 `CUtlProps` 包含內部屬性設定為的兩個成員: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) 和 [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。  
  
 如需屬性集對應的巨集的詳細資訊，請參閱 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md) 和 [END\_PROPSET\_MAP](../../data/oledb/end-propset-map.md)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)