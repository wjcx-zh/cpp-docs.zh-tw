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
ms.openlocfilehash: bf30f1b0aa83ef002337b76601f04c7103963441
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620736"
---
# <a name="class-library-overview"></a>類別庫概觀

此總覽會分類並描述 MFC 程式庫（MFC）9.0 版中的類別。 MFC 中的類別（結合在一起）構成應用程式架構，這是針對 Windows API 撰寫之應用程式的架構。 您的程式設計工作是填入您的應用程式特定的程式碼。

程式庫的類別會在這裡顯示為下列分類：

- [根類別：CObject](root-class-cobject.md)

- [MFC 應用程式架構類別](mfc-application-architecture-classes.md)

  - [應用程式和執行緒支援類別](application-and-thread-support-classes.md)

  - [命令路由類別](command-routing-classes.md)

  - [文件類別](document-classes.md)

  - [檢視類別 (架構)](view-classes-architecture.md)

  - [框架視窗類別 (架構)](frame-window-classes-architecture.md)

  - [文件樣板類別](document-template-classes.md)

- [視窗、對話方塊和控制項類別](window-dialog-and-control-classes.md)

  - [框架視窗類別 (Windows)](frame-window-classes-windows.md)

  - [檢視類別 (Windows)](view-classes-windows.md)

  - [對話方塊類別](dialog-box-classes.md)

  - [控制項類別](control-classes.md)

  - [控制列類別](control-bar-classes.md)

- [繪圖和列印類別](drawing-and-printing-classes.md)

  - [輸出(裝置內容) 類別](output-device-context-classes.md)

  - [繪圖工具類別](drawing-tool-classes.md)

- [簡單資料類型類別](simple-data-type-classes.md)

- [陣列、清單和對應類別](array-list-and-map-classes.md)

  - [陣列、清單和對應的樣板類別](template-classes-for-arrays-lists-and-maps.md)

  - [立即可用的陣列類別](ready-to-use-array-classes.md)

  - [立即可用的清單類別](ready-to-use-list-classes.md)

  - [立即可用的對應類別](ready-to-use-map-classes.md)

- [檔案和資料庫類別](file-and-database-classes.md)

  - [檔案 I/O 類別](file-i-o-classes.md)

  - [DAO 類別](dao-classes.md)

  - [ODBC 類別](odbc-classes.md)

  - [OLE DB 類別](ole-db-classes.md)

- [網際網路和網路類別](internet-and-networking-classes.md)

  - [Windows Sockets 類別](windows-sockets-classes.md)

  - [Win32 網際網路類別](win32-internet-classes.md)

- [OLE 類別](ole-classes.md)

  - [OLE 容器類別](ole-container-classes.md)

  - [OLE 伺服器類別](ole-server-classes.md)

  - [OLE 拖放和資料傳輸類別](ole-drag-and-drop-and-data-transfer-classes.md)

  - [OLE 通用對話方塊類別](ole-common-dialog-classes.md)

  - [OLE Automation 類別](ole-automation-classes.md)

  - [OLE 控制項類別](ole-control-classes.md)

  - [主動式文件類別](active-document-classes.md)

  - [OLE 相關類別](ole-related-classes.md)

- [偵錯和例外狀況類別](debugging-and-exception-classes.md)

  - [偵錯支援類別](debugging-support-classes.md)

  - [例外狀況類別](exception-classes.md)

[一般類別設計原理](general-class-design-philosophy.md)一節說明 MFC 程式庫的設計方式。

如需架構的總覽，請參閱[使用類別來撰寫適用于 Windows 的應用程式](using-the-classes-to-write-applications-for-windows.md)。 上面列出的部分類別是一般用途的類別，可以在架構之外使用，並提供有用的抽象概念，例如集合、例外狀況、檔案和字串。

若要查看類別的繼承，請使用類別階層架構[圖表](hierarchy-chart.md)。

除了此總覽中列出的類別之外，MFC 程式庫還包含許多全域函式、全域變數和宏。 [ [Mfc 宏] 和 [全域](reference/mfc-macros-and-globals.md)] 主題中有這些方法的總覽和詳細清單，其遵循 mfc 類別的字母順序參考。

## <a name="see-also"></a>另請參閱

[MFC 傳統型應用程式](mfc-desktop-applications.md)
