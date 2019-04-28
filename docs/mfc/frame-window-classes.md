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
ms.openlocfilehash: d42fa475fca7c92e4ba46b164a9beda9869231c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219778"
---
# <a name="frame-window-classes"></a>框架視窗類別

每個應用程式會有一個 「 主框架視窗 」 通常具有其標題中的 應用程式名稱的桌面視窗。 每份文件通常有一個 「 文件框架視窗 」。 文件框架視窗包含至少一個檢視，顯示文件的資料。

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 和 MDI 應用程式中的框架 Windows

SDI 應用程式，還有一個衍生自類別的框架視窗[CFrameWnd](../mfc/reference/cframewnd-class.md)。 此範圍是在主框架視窗和文件框架視窗。 對於 MDI 應用程式中，主框架視窗衍生自類別[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，和文件框架視窗，也就是 MDI 子視窗，衍生自類別[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。

## <a name="use-the-frame-window-class-or-derive-from-it"></a>使用框架視窗類別，或從它衍生

這些類別會提供大部分的應用程式所需的框架視窗功能。 一般情況下的預設行為與它們所提供的外觀會符合您的需求。 如果您需要額外的功能時，衍生自這些類別。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [應用程式精靈所建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

- [變更 MFC 所建立之視窗的樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>另請參閱

[框架視窗](../mfc/frame-windows.md)
