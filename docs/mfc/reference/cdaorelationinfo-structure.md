---
title: "CDaoRelationInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoRelationInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRelationInfo 結構"
  - "DAO (資料存取物件), 關聯性集合"
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoRelationInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

關聯的 `CDaoRelationInfo` 結構包含資訊定義在兩個資料表之間欄位在 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件中。  
  
## 語法  
  
```  
  
      struct CDaoRelationInfo  
{  
   CDaoRelationInfo( );                    // Constructor  
   CString m_strName;                      // Primary  
   CString m_strTable;                     // Primary  
   CString m_strForeignTable;              // Primary  
   long m_lAttributes;                     // Secondary  
   CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
   short m_nFields;                        // Secondary  
   // Below the // Implementation comment:  
   // Destructor, not otherwise documented  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一名稱相關聯的物件。  如需詳細資訊，請參閱本主題中的"名字屬性" DAO'幫助。  
  
 *m\_strTable*  
 在關聯將主資料表。  
  
 *m\_strForeignTable*  
 命名關聯對外資料表。  外部資料表是用於資料表的外部索引鍵。  通常，您會使用外部資料表建立或強制使用參考完整性。  外部資料表是一對多關聯性中表示「多」方。  外部資料表包含的範例資料表包含美國狀態或加拿大省或客戶訂單的程式碼。  
  
 `m_lAttributes`  
 包含相關聯型別的相關資訊。  這個成員的值可以是下列任何一項:  
  
-   **dbRelationUnique** 關聯性是一對一。  
  
-   **dbRelationDontEnforce** 關聯性不會強制執行 \(沒有參考完整性 \(Referential Integrity\)。  
  
-   **dbRelationInherited** 關係存在於包含兩種其他的資料表建立非目前的資料庫。  
  
-   **dbRelationLeft** 關聯性是左聯結。  左外部聯結包含任何資料錄開頭 \(左邊\) 這兩個資料表，因此，即使沒有資料錄相符的值在第二個 \(右邊\) 資料表中。  
  
-   **dbRelationRight** 關聯性是權限聯結。  右外部聯結包含任何資料錄第二個 \(右邊\) 這兩個資料表，因此，即使沒有資料錄相符的值在第一個 \(左邊\) 資料表中。  
  
-   **dbRelationUpdateCascade** 更新下拉式清單。  
  
-   **dbRelationDeleteCascade** 刪除將下拉式清單。  
  
 `m_pFieldInfos`  
 [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)結構陣列的指標。  陣列包含每個欄位的物件相關聯的。  `m_nFields` 資料成員指定陣列元素的計數。  
  
 `m_nFields`  
 `CDaoRelationFieldInfo` 數字在 `m_pFieldInfos` 資料成員的物件。  
  
## 備註  
 對主要和次要參考在指令的資訊如何由類別 `CDaoDatabase`的 [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成員函式傳回。  
  
 相關物件不是由 MFC 類別表示。  相反地，基礎 `CDaoDatabase` 類別之物件的 MFC DAO 物件維護相關聯物件的集合: `CDaoDatabase` 提供成員函式存取關聯資訊一些個別項目，也可以同時存取它們與 `CDaoRelationInfo` 物件藉由呼叫包含的資料庫物件的 `GetRelationInfo` 成員函式。  
  
 [CDaoDatabase::GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成員函式來擷取的資訊在 `CDaoRelationInfo` 結構中。  `CDaoRelationInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoRelationInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [CDaoRelationFieldInfo 結構](../../mfc/reference/cdaorelationfieldinfo-structure.md)