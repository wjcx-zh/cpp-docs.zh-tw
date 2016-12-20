---
title: "CDaoDatabaseInfo 結構 | Microsoft Docs"
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
  - "CDaoDatabaseInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoDatabaseInfo 結構"
  - "DAO (資料存取物件), 資料庫集合"
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoDatabaseInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoDatabaseInfo` 結構包含關於為資料存取物件 \(DAO\) 定義的資料庫物件的資訊。  
  
## 語法  
  
```  
  
      struct CDaoDatabaseInfo  
{  
   CString m_strName;       // Primary  
   BOOL m_bUpdatable;       // Primary  
   BOOL m_bTransactions;    // Primary  
   CString m_strVersion;    // Secondary  
   long m_lCollatingOrder;  // Secondary  
   short m_nQueryTimeout;   // Secondary  
   CString m_strConnect;    // All  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名資料庫物件。  直接擷取這個屬性，請呼叫 [CDaoDatabase::GetName](../Topic/CDaoDatabase::GetName.md)。  如需詳細資訊，請參閱本主題 DAO 說明的「Name 屬性」 。  
  
 `m_bUpdatable`  
 指出是否可以變更資料庫。  直接擷取這個屬性，請呼叫 [CDaoDatabase::CanUpdate](../Topic/CDaoDatabase::CanUpdate.md)。  如需詳細資訊，請參閱本主題 DAO 說明的「可更新屬性」。  
  
 *m\_bTransactions*  
 指出資料來源是否支援交易—稍後可以復原 \(取消\) 或做 \(儲存\) 的一系列變更的記錄。  如果資料庫使用 Microsoft Jet 資料庫引擎，交易屬性不是零，您也可以使用交易。  其他資料庫引擎可能不支援交易。  直接擷取這個屬性，請呼叫 [CDaoDatabase::CanTransact](../Topic/CDaoDatabase::CanTransact.md)。  如需詳細資訊，請參閱本主題 DAO 說明的「交易屬性」。  
  
 *m\_strVersion*  
 表示 Microsoft Jet 資料庫引擎的版本。  若要直接擷取這個屬性的值，請呼叫資料庫物件的 [GetName](../Topic/CDaoDatabase::GetVersion.md) 成員函式。  如需詳細資訊，請參閱本主題 DAO 說明的「版本屬性」 。  
  
 `m_lCollatingOrder`  
 在文字為字串比較和排序指定排序順序的序列。  可能的值包括：  
  
-   **dbSortGeneral** 使用一般 \(英文、法文、德文、葡萄牙、義大利文和現代西班牙文\) 的排序次序。  
  
-   **dbSortArabic** 使用阿拉伯文排序次序。  
  
-   **dbSortCyrillic** 使用俄文排序次序。  
  
-   **dbSortCzech** 使用捷克文排序次序。  
  
-   **dbSortDutch** 用使用荷蘭文排序次序。  
  
-   **dbSortGreek** 使用希臘文排序次序。  
  
-   **dbSortHebrew** 使用希伯來文排序次序。  
  
-   使用**dbSortHungarian** 使用匈牙利文排序次序。  
  
-   **dbSortIcelandic** 使用冰島的排序次序。  
  
-   **dbSortNorwdan** 使用挪威或丹麥排序次序。  
  
-   **dbSortPDXIntl** 使用衝突國際排序次序。  
  
-   **dbSortPDXNor** 使用衝突挪威或丹麥排序次序。  
  
-   **dbSortPDXSwe** 使用衝突瑞典或芬蘭排序次序。  
  
-   **dbSortPolish** 使用波蘭排序次序。  
  
-   **dbSortSpanish** 使用西班牙文排序次序。  
  
-   **dbSortSwedFin** 使用瑞典或芬蘭排序次序。  
  
-   **dbSortTurkish** 使用土耳其排序次序。  
  
-   **dbSortUndefined** 排序次序是未定義或未知的。  
  
 如需詳細資訊，請參閱 DAO 說明 \<自訂 Windows 資料存取的主題登錄設定\>。  
  
 *m\_nQueryTimeout*  
 當在 ODBC 資料庫執行查詢時，Microsoft Jet 資料庫引擎在逾時錯誤發生前等候的秒數。  預設逾時值為 60 秒。  當 QueryTimeout 設為 0 時，逾時不會發生；這可能會導致程式停止回應。  若要直接擷取這個屬性的值，請呼叫資料庫物件的 [GetQueryTimeout](../Topic/CDaoDatabase::GetQueryTimeout.md) 成員函式。  如需詳細資訊，請參閱本主題 DAO 說明的「QueryTimeout」。  
  
 `m_strConnect`  
 提供關於開放式資料庫來源的相關資訊。  如需連接字串的資訊以及有關直接擷取這個屬性值的詳細資訊，請參閱 [CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md) 成員函式。  如需詳細資訊，請參閱 DAO Help 中的「連線屬性」。  
  
## 備註  
 資料庫是建構類別 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)的 MFC 物件的 DAO 物件。  對主要、次要參考及上述所有都指出如何由類別 [CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md) 成員函式傳回資訊。  
  
 [CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md) 成員函式擷取的資訊儲存在 `CDaoDatabaseInfo` 結構中。  在其資料庫集合資料庫物件儲存為 `CDaoWorkspace` 物件呼叫 `GetDatabaseInfo`。  `CDaoDatabaseInfo` 也會在偵錯組建中定義 `Dump` 函式成員。  您可以使用 `Dump` 來傾印 `CDaoDatabaseInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace::GetDatabaseCount](../Topic/CDaoWorkspace::GetDatabaseCount.md)