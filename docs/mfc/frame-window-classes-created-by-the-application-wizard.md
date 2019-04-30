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
ms.openlocfilehash: 46da8fc0cb98406bdf97285d7c6f824afd61c4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392813"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>應用程式精靈所建立的框架視窗類別

當您建立新的 MFC 專案從**新的專案** 對話方塊中，除了應用程式、 文件和檢視類別，應用程式精靈 會建立您的應用程式主框架視窗的衍生的框架視窗類別。 此類別預設稱為 `CMainFrame`，包含此類別的檔案名稱為 MAINFRM.H 和 MAINFRM.CPP。

如果您的應用程式是 SDI，您`CMainFrame`類別衍生自類別[CFrameWnd](../mfc/reference/cframewnd-class.md)。

如果您的應用程式是 MDI`CMainFrame`衍生自類別[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)。 在此情況下，`CMainFrame` 會實作主框架，其中有功能表、工具列和狀態列。 [應用程式精靈] 不會為您衍生新的文件框架視窗類別。 相反地，它會使用中的預設實作[CMDIChildWnd 類別](../mfc/reference/cmdichildwnd-class.md)。 MFC 架構會建立子視窗，以包含應用程式所需的 `CScrollView`、`CEditView`、`CTreeView`、`CListView` 類型的各個檢視。 如果您需要自訂您的文件框架視窗，您可以建立新的文件框架視窗類別 (請參閱[加入類別](../ide/adding-a-class-visual-cpp.md))。

如果您選擇支援工具列，類別也具有成員變數的型別[CToolBar](../mfc/reference/ctoolbar-class.md)並[CStatusBar](../mfc/reference/cstatusbar-class.md)並`OnCreate`訊息處理常式函式來初始化兩個[控制列](../mfc/control-bars.md)。

這些框架視窗類別建立時即會運作，不過為了提高其功能，您必須新增成員變數和成員函式。 您也可以讓視窗類別處理其他 Windows 訊息。 如需詳細資訊，請參閱 <<c0> [ 變更 MFC 所建立的視窗樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>另請參閱

[框架視窗類別](../mfc/frame-window-classes.md)<br/>
[MFC 程式或控制項原始程式檔和標頭檔](../build/reference/mfc-program-or-control-source-and-header-files.md)

