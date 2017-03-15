---
title: "BEGIN_COLUMN_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_COLUMN_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_COLUMN_MAP 巨集"
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# BEGIN_COLUMN_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記資料行對應項目的開頭。  
  
## 語法  
  
```  
  
BEGIN_COLUMN_MAP(  
x  
 )  
  
```  
  
#### 參數  
 *x*  
 \[in\] 衍生自 `CAccessor` 之使用者資料錄類別的名稱。  
  
## 備註  
 如果資料列集上只有單一存取子，就會使用此巨集。 如果資料列集上有多個存取子，請使用 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)。  
  
 `BEGIN_COLUMN_MAP` 巨集會以 `END_COLUMN_MAP` 巨集完成。 當使用者資料錄中只需要一個存取子時，就會使用此巨集。  
  
 資料行會對應至您想要繫結之資料列集中的欄位。  
  
## 範例  
 以下是範例資料行和參數對應︰  
  
 [!CODE [NVC_OLEDB_Consumer#16](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#16)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN\_ENTRY\_EX](../../data/oledb/column-entry-ex.md)