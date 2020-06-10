---
title: 架構 (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: b02d5a1862a278f46591895f20f58a97367b5ab2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618790"
---
# <a name="framework-mfc"></a>架構 (MFC)

您會使用 MFC 程式庫架構進行的工作有很大部分是基於一些主要類別和數個 Visual C++ 工具。 某些類別會封裝大部分的 Win32 應用程式開發介面 (API)。 其他類別會封裝應用程式概念 (例如文件、檢視和應用程式本身)。 而其餘的類別則會封裝 OLE 功能、ODBC 和 DAO 資料存取功能。  （DAO 可透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。）

例如，視窗的 Win32 概念是由 MFC 類別 `CWnd` 所封裝。 也就是說，一個名為 `CWnd` 的 C++ 類別會封裝或「包裝」代表 Windows 視窗的 `HWND` 控制代碼。 同樣地，類別 `CDialog` 會封裝 Win32 對話方塊。

封裝表示 C++ 類別 (例如 `CWnd`) 包含 `HWND` 類型的成員變數，而類別的成員函式則是會封裝對採用 `HWND` 做為參數的 Win32 函式呼叫。 類別成員函式通常與它們所封裝的 Win32 函式具有相同名稱。

## <a name="in-this-section"></a>本節內容

[SDI 和 MDI](sdi-and-mdi.md)

[文件、檢視和架構](documents-views-and-the-framework.md)

[精靈和資源編輯器](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>相關章節

[在架構上建置](building-on-the-framework.md)

[架構如何呼叫您的程式碼](how-the-framework-calls-your-code.md)

[CWinApp：應用程式類別](cwinapp-the-application-class.md)

[檔範本和檔/視圖建立程式](document-templates-and-the-document-view-creation-process.md)

[訊息處理和對應](message-handling-and-mapping.md)

[視窗物件](window-objects.md)

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](using-the-classes-to-write-applications-for-windows.md)
