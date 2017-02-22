---
title: "例外狀況處理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (資料存取物件), 例外狀況"
  - "例外狀況巨集"
  - "例外狀況, MFC 擲回函式"
  - "例外狀況, 處理"
  - "巨集, 例外狀況處理"
  - "MFC, 例外狀況"
  - "OLE 例外狀況, MFC 函式"
  - "終止函式, MFC"
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# 例外狀況處理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當程式執行時，稱為「例外狀況」的一些異常條件和錯誤可能發生。  這些可能包括記憶體不足、資源配置錯誤和找不到檔案。  
  
 MFC 程式庫使用嚴格地在 C\+\+ 的美國國家標準學習標準委員會送出的那個模式化的一份例外狀況處理機制。  例外處理常式必須在呼叫可能會遇到一個異常情況的函式之前所設定。  如果函式有一個異常條件，則會擲回例外狀況，且控制項傳遞給例外處理常式。  
  
 數個巨集隨附 MFC 程式庫將設定例外處理常式。  必要時許多其他全域函式說明擲回特定例外狀況並結束程式。  這些巨集和全域函式可分類如下:  
  
-   [例外狀況巨集](#_mfc_exception_macros)，建構您的例外處理常式。  
  
-   [例外狀況擲回的函式](#_mfc_exception.2d.throwing_functions)，以產生特定型別的例外狀況。  
  
-   [終止函式](#_mfc_termination_functions)，讓程式終止。  
  
 如需範例和詳細資訊，請參閱本文件的 [例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### 例外狀況巨集  
  
|||  
|-|-|  
|[TRY](../Topic/TRY.md)|指定程式碼區塊例外狀況處理。|  
|[CATCH](../Topic/CATCH.md)|指定程式碼區塊攔截的例外狀況從前面 **TRY** 區塊。|  
|[CATCH\_ALL](../Topic/CATCH_ALL.md)|指定程式碼區塊攔截的所有例外狀況從前面 **TRY** 區塊。|  
|[AND\_CATCH](../Topic/AND_CATCH.md)|從前面 **TRY** 區塊指定程式碼區塊攔截的例附加例外狀況類別。|  
|[AND\_CATCH\_ALL](../Topic/AND_CATCH_ALL.md)|指定可在一個 **TRY** 區塊擲回的攔截所有其他例外狀況型別的程式碼區塊。|  
|[END\_CATCH](../Topic/END_CATCH.md)|結束最後 **CATCH** 或 `AND_CATCH` 程式碼區塊。|  
|[END\_CATCH\_ALL](../Topic/END_CATCH_ALL.md)|結束時為 `CATCH_ALL` 程式碼區塊。|  
|[THROW](../Topic/THROW%20\(MFC\).md)|擲回指定的例外狀況。|  
|[THROW\_LAST](../Topic/THROW_LAST.md)|擲回目前未處理的例外狀況給外部處理常式。|  
  
### 擲回例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowArchiveException](../Topic/AfxThrowArchiveException.md)|擲回的例外狀況。|  
|[AfxThrowFileException](../Topic/AfxThrowFileException.md)|擲回檔案例外。|  
|[AfxThrowMemoryException](../Topic/AfxThrowMemoryException.md)|擲回記憶體不足例外狀況。|  
|[AfxThrowNotSupportedException](../Topic/AfxThrowNotSupportedException.md)|擲回一個不支援例外狀況。|  
|[AfxThrowResourceException](../Topic/AfxThrowResourceException.md)|擲回 Windows 資源非找到例外狀況。|  
|[AfxThrowUserException](../Topic/AfxThrowUserException.md)|擲回在一次使用者啟始的程式動作的例外狀況。|  
  
 MFC 提供 OLE 例外狀況特別提供兩種例外狀況擲回的函式:  
  
### OLE 例外狀況函式  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md)|擲回在 OLE Automation 函式內的例外狀況。|  
|[AfxThrowOleException](../Topic/AfxThrowOleException.md)|擲回 OLE 例外狀況。|  
  
 為了支援資料庫例外狀況，資料庫類別提供兩種例外狀況類別、 `CDBException` 和 `CDaoException`和全域函式支援例外狀況類型:  
  
### DAO 例外狀況函式  
  
|||  
|-|-|  
|[AfxThrowDAOException](../Topic/AfxThrowDaoException.md)|擲回從您的程式碼的 [CDaoException](../../mfc/reference/cdaoexception-class.md) 。|  
|[AfxThrowDBException](../Topic/AfxThrowDBException.md)|擲回從您的程式碼的 [CDBException](../../mfc/reference/cdbexception-class.md) 。|  
  
 MFC 提供下列終止函式:  
  
### 終止函式  
  
|||  
|-|-|  
|[AfxAbort](../Topic/AfxAbort.md)|呼叫結束應用程式，發生嚴重錯誤。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException Class](../../mfc/reference/cexception-class.md)