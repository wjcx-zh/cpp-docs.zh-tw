---
title: 框架視窗類別
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: ffa5b966ee042120213896dc7ad9d81c048ef928
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625803"
---
# <a name="frame-window-classes"></a>框架視窗類別

每個應用程式都有一個「主框架視窗」，通常在標題中有應用程式名稱的桌面視窗。 每個檔通常會有一個「檔框架視窗」。 檔框架視窗至少包含一個 view，其中呈現檔的資料。

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 和 MDI 應用程式中的框架視窗

針對 SDI 應用程式，有一個衍生自類別[CFrameWnd](reference/cframewnd-class.md)的框架視窗。 此視窗同時是主框架視窗和檔框架視窗。 若是 MDI 應用程式，主框架視窗是衍生自類別[CMDIFrameWnd](reference/cmdiframewnd-class.md)，而檔框架視窗（也就是 MDI 子視窗）則是從類別[CMDIChildWnd](reference/cmdichildwnd-class.md)衍生而來。

## <a name="use-the-frame-window-class-or-derive-from-it"></a>使用框架視窗類別，或從中衍生

這些類別會為您的應用程式提供您所需的大部分框架視窗功能。 在正常情況下，它們所提供的預設行為和外觀會符合您的需求。 如果您需要其他功能，請從這些類別衍生。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [應用程式精靈所建立的框架視窗類別](frame-window-classes-created-by-the-application-wizard.md)

- [框架視窗樣式](frame-window-styles-cpp.md)

- [變更 MFC 所建立之視窗的樣式](changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>另請參閱

[框架視窗](frame-windows.md)
