---
title: "CDaoWorkspaceInfo 結構 | Microsoft Docs"
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
  - "CDaoWorkspaceInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoWorkspaceInfo 結構"
  - "DAO (資料存取物件), 工作區集合"
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoWorkspaceInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoWorkspaceInfo` 結構包含用於資料存取物件 \(DAO\) 資料庫存取定義的工作區的相關資訊。  
  
## 語法  
  
```  
  
      struct CDaoWorkspaceInfo  
{  
   CString m_strName;           // Primary  
   CString m_strUserName;       // Secondary  
   BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名工作區物件。  若要直接擷取這個屬性的值，請呼叫 querydef 物件的 [GetName](../Topic/CDaoQueryDef::GetName.md) 成員函式。  如需詳細資訊，請參閱本主題中的"名字屬性" DAO'幫助。  
  
 *m\_strUserName*  
 表示工作區物件的擁有者的值。  如需相關資訊，請參閱本主題 \< 使用者名稱屬性 DAO 說明。  
  
 *m\_bIsolateODBCTrans*  
 值指示涉及相同 ODBC 資料庫的多重商務處理是否隔離。  如需詳細資訊，請參閱 [CDaoWorkspace::SetIsolateODBCTrans](../Topic/CDaoWorkspace::SetIsolateODBCTrans.md)。  如需相關資訊，請參閱本主題 solateODBCTrans 屬性 DAO 說明。  
  
## 備註  
 工作區是類別 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。  對主要，次要參考和所有在指令的資訊如何由類別 `CDaoWorkspace`的 [GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md) 成員函式傳回。  
  
 [CDaoWorkspace::GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md) 成員函式來擷取的資訊在 `CDaoWorkspaceInfo` 結構中。  `CDaoWorkspaceInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoWorkspaceInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)