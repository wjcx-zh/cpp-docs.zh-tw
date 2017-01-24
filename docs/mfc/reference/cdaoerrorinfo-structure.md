---
title: "CDaoErrorInfo 結構 | Microsoft Docs"
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
  - "CDaoErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoErrorInfo 結構"
  - "DAO (資料存取物件), 錯誤集合"
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoErrorInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoErrorInfo` 結構包含用於資料存取物件定義的錯誤物件的資訊 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoErrorInfo  
{  
   long m_lErrorCode;  
   CString m_strSource;  
   CString m_strDescription;  
   CString m_strHelpFile;  
   long m_lHelpContext;  
};  
```  
  
#### 參數  
 *m\_lErrorCode*  
 數值 DAO 錯誤碼。  請參閱本主題 \< 可資料存取錯誤 DAO 說明。  
  
 *m\_strSource*  
 最初產生錯誤的物件或應用程式的名稱。  來源屬性指定表示最初造成錯誤之物件的字串運算式;運算式通常是物件的類別名稱。  如需詳細資訊，請參閱本主題 \< 來源屬性 DAO 說明。  
  
 *m\_strDescription*  
 說明字串與錯誤。  如需詳細資訊，請參閱這個主題說明屬性 DAO 說明。  
  
 *m\_strHelpFile*  
 的完整路徑 \(Microsoft Windows 說明檔。  如需詳細資訊，請參閱本主題 \< HelpContext， HelpFile 屬性 DAO 說明。  
  
 *m\_lHelpContext*  
 一個主題的內容 ID 在 Microsoft Windows 說明檔。  如需詳細資訊，請參閱本主題 \< HelpContext， HelpFile 屬性 DAO 說明。  
  
## 備註  
 MFC 不封裝在類別的 DAO 錯誤物件。  相反地， [CDaoException](../../mfc/reference/cdaoexception-class.md) 類別提供存取的錯誤集合包含一個介面 DAO **DBEngine** 物件，也包含所有工作區的物件。  在 MFC DAO 作業擲回您攔截 `CDaoException` 物件時， MFC 在例外狀況物件的 [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 成員填滿 `CDaoErrorInfo` 結構並儲存它。\(如果您選擇直接呼叫 DAO，您必須呼叫例外狀況物件的 [GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) 成員函式來填滿 `m_pErrorInfo`\)。  
  
 如需處理 DAO 錯誤的詳細資訊，請參閱本文件的 [例外狀況:資料庫例外狀況。](../../mfc/exceptions-database-exceptions.md)。  如需相關資訊，請參閱主題錯誤物件 DAO 說明。  
  
 [CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) 成員函式來擷取的資訊在 `CDaoErrorInfo` 結構中。  檢查從您在例外處理常式攔截 `CDaoException` 物件的 [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 資料成員，或從您明確建立以檢查錯誤可能發生在的直接呼叫期間加入至 DAO 之 `CDaoException` 物件的呼叫 `GetErrorInfo` 連接。  `CDaoErrorInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoErrorInfo` 物件的內容。  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)