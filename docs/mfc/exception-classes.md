---
title: "例外狀況類別 | Microsoft Docs"
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
  - "vc.classes.exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "例外狀況類別"
  - "例外狀況處理, 例外狀況類別"
  - "MFC, 例外狀況"
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別庫提供根據類別的例外狀況處理機制 `CException`。  應用程式架構在它的程式碼使用例外狀況;您也可以使用它們。  如需詳細資訊，請參閱 [Exceptions](../mfc/exception-handling-in-mfc.md) 主題。  您可以從 `CException`衍生您自己的例外狀況型別。  
  
 MFC 提供您可以衍生您自己的例外狀況和例外狀況類別的所有例外狀況支援的例外狀況類別。  
  
 [CException](../mfc/reference/cexception-class.md)  
 適用於例外狀況的基底類別。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 封存例外狀況。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 例外狀況造成 DAO 資料庫作業失敗。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 例外狀況造成 ODBC 資料庫處理失敗。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 物件資料的例外狀況。  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 記憶體不足例外狀況  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 例外狀況是因為使用不支援的功能。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 例外狀況造成 OLE 處理失敗。  容器和伺服器會使用這個類別。  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 在自動化時造成的錯誤的例外狀況。  Automation 例外狀況由 Automation 伺服器擲回並由 Automation 用戶端攔截。  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 例外狀況是因為載入的 Windows 資源錯誤。  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 用於例外狀況會使用使用者啟動的作業。  通常，在此情況下，在擲回這個例外狀況之前，使用者會收到了這個問題。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)