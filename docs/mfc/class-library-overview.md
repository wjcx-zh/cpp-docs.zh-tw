---
title: 類別庫概觀
ms.date: 09/17/2019
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
ms.openlocfilehash: 9b307c4993a1a7a397741864381c0739a1f4c4ea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374582"
---
# <a name="class-library-overview"></a>類別庫概觀

此概述對 Microsoft 基礎類庫 (MFC) 版本 9.0 中的類進行分類和描述。 MFC 中的類組合在一起構成了一個應用程式框架,即為 Windows API 編寫的應用程式的框架。 程式設計任務是填寫特定於應用程式的代碼。

函式庫的類別以以下類別顯示:

- [根類別：CObject](../mfc/root-class-cobject.md)

- [MFC 應用程式架構類別](../mfc/mfc-application-architecture-classes.md)

  - [應用程式和執行緒支援類別](../mfc/application-and-thread-support-classes.md)

  - [命令路由類別](../mfc/command-routing-classes.md)

  - [文件類別](../mfc/document-classes.md)

  - [檢視類別 (架構)](../mfc/view-classes-architecture.md)

  - [框架視窗類別 (架構)](../mfc/frame-window-classes-architecture.md)

  - [文件樣板類別](../mfc/document-template-classes.md)

- [視窗、對話方塊和控制項類別](../mfc/window-dialog-and-control-classes.md)

  - [框架視窗類別 (Windows)](../mfc/frame-window-classes-windows.md)

  - [檢視類別 (Windows)](../mfc/view-classes-windows.md)

  - [對話方塊類別](../mfc/dialog-box-classes.md)

  - [控制項類別](../mfc/control-classes.md)

  - [控制列類別](../mfc/control-bar-classes.md)

- [繪圖和列印類別](../mfc/drawing-and-printing-classes.md)

  - [輸出(裝置內容) 類別](../mfc/output-device-context-classes.md)

  - [繪圖工具類別](../mfc/drawing-tool-classes.md)

- [簡單資料類型類別](../mfc/simple-data-type-classes.md)

- [陣列、清單和對應類別](../mfc/array-list-and-map-classes.md)

  - [陣列、清單和對應的樣板類別](../mfc/template-classes-for-arrays-lists-and-maps.md)

  - [立即可用的陣列類別](../mfc/ready-to-use-array-classes.md)

  - [立即可用的清單類別](../mfc/ready-to-use-list-classes.md)

  - [立即可用的對應類別](../mfc/ready-to-use-map-classes.md)

- [檔案和資料庫類別](../mfc/file-and-database-classes.md)

  - [檔案 I/O 類別](../mfc/file-i-o-classes.md)

  - [DAO 類別](../mfc/dao-classes.md)

  - [ODBC 類別](../mfc/odbc-classes.md)

  - [OLE DB 類別](../mfc/ole-db-classes.md)

- [網際網路和網路類別](../mfc/internet-and-networking-classes.md)

  - [Windows Sockets 類別](../mfc/windows-sockets-classes.md)

  - [Win32 網際網路類別](../mfc/win32-internet-classes.md)

- [OLE 類別](../mfc/ole-classes.md)

  - [OLE 容器類別](../mfc/ole-container-classes.md)

  - [OLE 伺服器類別](../mfc/ole-server-classes.md)

  - [OLE 拖放和資料傳輸類別](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)

  - [OLE 通用對話方塊類別](../mfc/ole-common-dialog-classes.md)

  - [OLE Automation 類別](../mfc/ole-automation-classes.md)

  - [OLE 控制項類別](../mfc/ole-control-classes.md)

  - [主動式文件類別](../mfc/active-document-classes.md)

  - [OLE 相關類別](../mfc/ole-related-classes.md)

- [偵錯和例外狀況類別](../mfc/debugging-and-exception-classes.md)

  - [偵錯支援類別](../mfc/debugging-support-classes.md)

  - [例外狀況類別](../mfc/exception-classes.md)

"[一般類設計理念"](../mfc/general-class-design-philosophy.md)部分解釋了 MFC 庫的設計方式。

有關框架的概述,請參閱[使用類為 Windows 編寫應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。 上面列出的一些類是通用類,可以在框架之外使用,並提供有用的抽象,如集合、異常、檔和字串。

要檢視類別的繼承,請使用[類別結構圖表](../mfc/hierarchy-chart.md)。

除了此概述中列出的類外,MFC 庫還包含許多全域函數、全域變數和宏。 在主題[MFC 宏和全域](../mfc/reference/mfc-macros-and-globals.md)中,有這些概述和詳細清單,其遵循 MFC 類的字母順序引用。

## <a name="see-also"></a>另請參閱

[MFC 傳統型應用程式](../mfc/mfc-desktop-applications.md)
