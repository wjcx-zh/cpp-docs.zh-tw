---
title: 應用程式精靈所建立的框架視窗類別
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
ms.openlocfilehash: 00254bdf49015f26ac257789a15afd1e7f5cc31f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621700"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>應用程式精靈所建立的框架視窗類別

當您從 [**新增專案**] 對話方塊建立新的 MFC 專案時，除了 [應用程式]、[檔] 和 [視圖] 類別之外，應用程式精靈也會為應用程式的主框架視窗建立衍生的框架視窗類別。 此類別預設稱為 `CMainFrame`，包含此類別的檔案名稱為 MAINFRM.H 和 MAINFRM.CPP。

如果您的應用程式是 SDI，則您的 `CMainFrame` 類別衍生自類別[CFrameWnd](reference/cframewnd-class.md)。

如果您的應用程式是 MDI， `CMainFrame` 則衍生自類別[CMDIFrameWnd](reference/cmdiframewnd-class.md)。 在此情況下，`CMainFrame` 會實作主框架，其中有功能表、工具列和狀態列。 [應用程式精靈] 不會為您衍生新的文件框架視窗類別。 相反地，它會使用[CMDIChildWnd 類別](reference/cmdichildwnd-class.md)中的預設實值。 MFC 架構會建立子視窗，以包含應用程式所需的 `CScrollView`、`CEditView`、`CTreeView`、`CListView` 類型的各個檢視。 如果您需要自訂檔框架視窗，您可以建立新的檔框架視窗類別（請參閱[新增類別](../ide/adding-a-class-visual-cpp.md)）。

如果您選擇支援工具列，類別也會有[CToolBar](reference/ctoolbar-class.md)和[CStatusBar](reference/cstatusbar-class.md)類型的成員變數，以及用 `OnCreate` 來初始化兩個[控制](control-bars.md)列的訊息處理常式函式。

這些框架視窗類別建立時即會運作，不過為了提高其功能，您必須新增成員變數和成員函式。 您也可以讓視窗類別處理其他 Windows 訊息。 如需詳細資訊，請參閱[變更 MFC 所建立之視窗的樣式](changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>另請參閱

[框架視窗類別](frame-window-classes.md)<br/>
[MFC 程式或控制項來源和標頭檔](../build/reference/mfc-program-or-control-source-and-header-files.md)
