---
title: 例外狀況類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.exception
dev_langs:
- C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ce4085d0f5f2dcc73d126d04b7560ef8360ffd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exception-classes"></a>例外狀況類別
類別庫提供根據類別 `CException` 的例外狀況處理機制。 應用程式架構用其程式碼使用例外狀況，而您也可以用您的程式碼來使用例外狀況。 如需詳細資訊，請參閱文章[例外狀況](../mfc/exception-handling-in-mfc.md)。 您可以從 `CException`衍生您自己的例外狀況類型。  
  
 MFC 提供可以讓您自其衍生自己之例外狀況的例外狀況類別，以及其支援之所有例外狀況的例外狀況類別。  
  
 [CException](../mfc/reference/cexception-class.md)  
 例外狀況的基底類別。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 封存例外狀況。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 因 DAO 資料庫作業失敗而產生的例外狀況。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 因 ODBC 資料庫處理失敗而產生的例外狀況。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 檔案導向的例外狀況。  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 記憶體不足例外狀況。  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 因使用不支援的功能而產生的例外狀況。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 因自動化期間的錯誤而產生的例外狀況。 Automation 例外狀況由 Automation 伺服程式擲回，並由 Automation 用戶端攔截。  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 因載入 Windows 資源錯誤而產生的例外狀況。  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 用於停止使用者啟始之作業的例外狀況。 通常，在擲回這個例外狀況之前會先通知使用者此問題。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

