---
title: "CDaoRelationFieldInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoRelationFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRelationFieldInfo 結構"
  - "DAO (資料存取物件), 關聯性集合"
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoRelationFieldInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoRelationFieldInfo` 結構中為資料存取物件定義的關聯包含欄位的資訊 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoRelationFieldInfo  
{  
   CString m_strName;           // Primary  
   CString m_strForeignName;    // Primary  
};  
```  
  
#### 參數  
 `m_strName`  
 欄位名稱在關聯的主要資料表中。  
  
 `m_strForeignName`  
 欄位名稱在關聯的外部資料表中。  
  
## 備註  
 DAO 關聯物件在主要資料表中指定欄位和定義關聯性的欄位外部資料表中。  對主要的參考在結構描述定義上述指示資訊如何在呼叫衍生 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 物件的 `m_pFieldInfos` 成員傳回 `CDaoDatabase`類別的 [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成員函式。  
  
 使物件與欄位物件不是由 MFC 類別表示。  相反地，基礎類別包含 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 的 MFC 物件 DAO 物件關聯的物件集合，呼叫關聯集合。  每個關聯物件，接著，包含關聯欄位物件的集合。  每個關聯欄位物件在主要資料表中的外部資料表中與欄位與欄位。  採用一起，使欄位物件定義每個欄位的群組中每個資料表中，一起定義關聯性。  `CDaoDatabase` 可讓您存取與 `CDaoRelationInfo` 相關聯的物件呼叫 `GetRelationInfo` 成員函式物件。  `CDaoRelationInfo` 物件，然後，有一個資料成員，則為 `m_pFieldInfos`，指向 `CDaoRelationFieldInfo` 物件的陣列。  
  
 呼叫關聯集合中儲存關聯物件所需的包含 `CDaoDatabase` 物件的 [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成員函式中。  然後存取 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 物件的 `m_pFieldInfos` 成員。  `CDaoRelationFieldInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoRelationFieldInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo 結構](../../mfc/reference/cdaorelationinfo-structure.md)