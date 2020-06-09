---
title: 例外狀況類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.exception
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
ms.openlocfilehash: 907b34b12ffdaa70c4377a1012a66662fbba12d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619526"
---
# <a name="exception-classes"></a>例外狀況類別

類別庫提供根據類別 `CException` 的例外狀況處理機制。 應用程式架構用其程式碼使用例外狀況，而您也可以用您的程式碼來使用例外狀況。 如需詳細資訊，請參閱[例外](exception-handling-in-mfc.md)狀況。 您可以從 `CException`衍生您自己的例外狀況類型。

MFC 提供可以讓您自其衍生自己之例外狀況的例外狀況類別，以及其支援之所有例外狀況的例外狀況類別。

[CException](reference/cexception-class.md)<br/>
例外狀況的基底類別。

[CArchiveException](reference/carchiveexception-class.md)<br/>
封存例外狀況。

[CDaoException](reference/cdaoexception-class.md)<br/>
因 DAO 資料庫作業失敗而產生的例外狀況。

[CDBException](reference/cdbexception-class.md)<br/>
因 ODBC 資料庫處理失敗而產生的例外狀況。

[CFileException](reference/cfileexception-class.md)<br/>
檔案導向的例外狀況。

[CMemoryException](reference/cmemoryexception-class.md)<br/>
記憶體不足例外狀況。

[CNotSupportedException](reference/cnotsupportedexception-class.md)<br/>
因使用不支援的功能而產生的例外狀況。

[COleException](reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
因自動化期間的錯誤而產生的例外狀況。 Automation 例外狀況由 Automation 伺服程式擲回，並由 Automation 用戶端攔截。

[CResourceException](reference/cresourceexception-class.md)<br/>
因載入 Windows 資源錯誤而產生的例外狀況。

[CUserException](reference/cuserexception-class.md)<br/>
用於停止使用者啟始之作業的例外狀況。 通常，在擲回這個例外狀況之前會先通知使用者此問題。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
