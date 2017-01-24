---
title: "BEGIN_PROVIDER_COLUMN_MAP | Microsoft Docs"
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
  - "BEGIN_PROVIDER_COLUMN_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_PROVIDER_COLUMN_MAP 巨集"
ms.assetid: 506b8c0f-6be9-4c97-ba81-c4b7f7d428fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BEGIN_PROVIDER_COLUMN_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標籤提供者資料行對應項目的開頭。  
  
## 語法  
  
```  
  
BEGIN_PROVIDER_COLUMN_MAP(  
theClass   
)  
  
```  
  
#### 參數  
 `theClass`  
 \[in\] 類別的名稱對應所屬。  
  
## 範例  
 這個範例提供者資料行對應:  
  
 [!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/CPP/begin-provider-column-map_1.h)]  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)