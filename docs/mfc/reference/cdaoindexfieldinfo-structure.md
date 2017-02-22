---
title: "CDaoIndexFieldInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoIndexFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoIndexFieldInfo 結構"
  - "DAO (資料存取物件), 索引欄位集合"
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDaoIndexFieldInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoIndexFieldInfo` 結構中為資料存取物件定義的物件包含一個索引欄位物件的資訊 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoIndexFieldInfo  
{  
   CString m_strName;          // Primary  
   BOOL m_bDescending;         // Primary  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名索引欄位物件。  如需詳細資訊，請參閱本主題「Name 屬性」 DAO 說明。  
  
 *m\_bDescending*  
 表示索引物件定義的索引順序。  停止命令則為**TRUE** 。  
  
## 備註  
 索引物件可能有一些欄位，表示哪些欄位 tabledef \(或根據資料表的資料錄集\) 索引。  對主要上面指令的參考資訊如何在呼叫衍生 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 物件的 `m_pFieldInfos` 成員傳回類別 [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md) 或 [CDaoRecordset](../Topic/CDaoRecordset::GetIndexInfo.md)的 `GetIndexInfo` 成員函式。  
  
 索引物件和索引欄位物件不是由 MFC 類別表示。  相反地，基礎類別 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 中的 MFC 物件 DAO 物件中之物件的集合，稱為索引集合。  每個索引物件，一一接著，包含欄位的物件集合。  這些類別提供成員函式存取索引資訊一些個別項目也可以同時存取它們與 `CDaoIndexInfo` 物件藉由呼叫包含的 `GetIndexInfo` 物件的成員函式。  `CDaoIndexInfo` 物件，然後，有一個資料成員，則為 `m_pFieldInfos`，指向 `CDaoIndexFieldInfo` 物件的陣列。  
  
 呼叫索引集合中儲存索引物件所需的包含 tabledef 或資料錄集物件的 `GetIndexInfo` 成員函式中。  然後存取 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 物件的 `m_pFieldInfos` 成員。  `m_pFieldInfos` 陣列的長度儲存於 `m_nFields`中。  `CDaoIndexFieldInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoIndexFieldInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)   
 [CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)