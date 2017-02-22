---
title: "BEGIN_ACCESSOR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_ACCESSOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_ACCESSOR 巨集"
  - "BEGIN_ACCESSOR 巨集, 語法"
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# BEGIN_ACCESSOR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存取子標記項目的開頭。  
  
## 語法  
  
```  
  
BEGIN_ACCESSOR(  
num  
,   
bAuto  
 )  
  
```  
  
#### 參數  
 *num*  
 \[in\] 對這個存取子對應的存取子的零位移數字。  
  
 *bAuto*  
 \[in\] 指定存取子是否為自動存取子或手動存取子。  如果 **true**，存取子是自動；如果 **false**，存取子是手動的。  一個自動存取子表示資料為您擷取移動作業。  
  
## 備註  
 在對於資料列集的多重存取子的情況下，您需要指定 `BEGIN_ACCESSOR_MAP` 和為個別存取子使用 `BEGIN_ACCESSOR` 巨集。  `BEGIN_ACCESSOR` 巨集與 `END_ACCESSOR` 巨集完成。  `BEGIN_ACCESSOR_MAP` 巨集完成與 `END_ACCESSOR_MAP` 巨集。  
  
## 範例  
 請參閱 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [END\_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)