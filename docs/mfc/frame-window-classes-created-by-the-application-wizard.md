---
title: 應用程式精靈所建立的框架視窗類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CMainFrame
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3446de072266fdf7661d2e8d8ca0fc968279646
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>應用程式精靈所建立的框架視窗類別
當您使用[應用程式精靈](../ide/creating-desktop-projects-by-using-application-wizards.md)應用程式精靈建立基本架構應用程式，應用程式、 文件和檢視類別，除了建立應用程式的主框架視窗的衍生的框架視窗類別。 此類別預設稱為 `CMainFrame`，包含此類別的檔案名稱為 MAINFRM.H 和 MAINFRM.CPP。  
  
 如果您的應用程式是 SDI，您`CMainFrame`類別衍生自類別[CFrameWnd](../mfc/reference/cframewnd-class.md)。  
  
 如果您的應用程式是 MDI，`CMainFrame`衍生自類別[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)。 在此情況下，`CMainFrame` 會實作主框架，其中有功能表、工具列和狀態列。 [應用程式精靈] 不會為您衍生新的文件框架視窗類別。 相反地，它會使用中的預設實作[CMDIChildWnd 類別](../mfc/reference/cmdichildwnd-class.md)。 MFC 架構會建立子視窗，以包含應用程式所需的 `CScrollView`、`CEditView`、`CTreeView`、`CListView` 類型的各個檢視。 如果您需要自訂您的文件框架視窗，您可以建立新的文件框架視窗類別 (請參閱[將類別加入](../ide/adding-a-class-visual-cpp.md))。  
  
 如果您選擇支援工具列，類別也會有類型的成員變數[CToolBar](../mfc/reference/ctoolbar-class.md)和[CStatusBar](../mfc/reference/cstatusbar-class.md)和`OnCreate`訊息處理常式函式來初始化這兩個[控制列](../mfc/control-bars.md)。  
  
 這些框架視窗類別建立時即會運作，不過為了提高其功能，您必須新增成員變數和成員函式。 您也可以讓視窗類別處理其他 Windows 訊息。 如需詳細資訊，請參閱[變更 MFC 所建立的視窗樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [框架視窗類別](../mfc/frame-window-classes.md)   
 [MFC 程式或控制項原始程式檔和標頭檔](../ide/mfc-program-or-control-source-and-header-files.md)

