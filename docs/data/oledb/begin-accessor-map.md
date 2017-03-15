---
title: "BEGIN_ACCESSOR_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_ACCESSOR_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_ACCESSOR_MAP 巨集"
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# BEGIN_ACCESSOR_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記存取子對應項目的開頭。  
  
## 語法  
  
```  
  
BEGIN_ACCESSOR_MAP(  
x  
,   
num  
 )  
  
```  
  
#### 參數  
 *x*  
 \[in\] 使用者資料錄類別的名稱。  
  
 *num*  
 \[in\] 此存取子對應中的存取子數目。  
  
## 備註  
 如果資料列集上有多個存取子，您必須在開頭指定 `BEGIN_ACCESSOR_MAP`，並針對每個個別存取子使用 `BEGIN_ACCESSOR` 巨集。`BEGIN_ACCESSOR` 巨集會以 `END_ACCESSOR` 巨集完成。 存取子對應會以 `END_ACCESSOR_MAP` 巨集完成。  
  
 如果使用者資料錄中只有一個存取子，請使用巨集 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)。  
  
## 範例  
 [!CODE [NVC_OLEDB_Consumer#15](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#15)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)