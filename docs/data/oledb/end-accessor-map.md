---
title: "END_ACCESSOR_MAP | Microsoft Docs"
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
  - "END_ACCESSOR_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "END_ACCESSOR_MAP 巨集"
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# END_ACCESSOR_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記存取子對應項目的結尾。  
  
## 語法  
  
```  
  
END_ACCESSOR_MAP( )  
  
```  
  
## 備註  
 對於資料列集的多重存取子，您需要指定 `BEGIN_ACCESSOR_MAP` 和為個別存取子使用 `BEGIN_ACCESSOR` 巨集。  `BEGIN_ACCESSOR` 巨集完成與 `END_ACCESSOR` 巨集。  `BEGIN_ACCESSOR_MAP` 巨集完成與 `END_ACCESSOR_MAP` 巨集。  
  
## 範例  
 請參閱 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)