---
title: 框架視窗類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b9003ba503e0a78e5f223e766346d63679d9959
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="frame-window-classes"></a>框架視窗類別
每個應用程式有一個 「 主框架視窗，」 通常具有其標題中的 應用程式名稱的桌面視窗。 每份文件通常有一個 「 文件框架視窗 」。 文件框架視窗包含至少一個檢視，其呈現文件的資料。  
  
## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 和 MDI 應用程式中的框架視窗  
 SDI 應用程式，沒有一個衍生自類別的框架視窗[CFrameWnd](../mfc/reference/cframewnd-class.md)。 此視窗是主框架視窗和文件框架視窗。 主框架視窗的 MDI 應用程式中，衍生自類別[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，以及文件框架視窗，也就是 MDI 子視窗、 衍生自類別[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。  
  
## <a name="use-the-frame-window-class-or-derive-from-it"></a>使用框架視窗類別或衍生自  
 這些類別會提供大部分的應用程式所需的框架視窗功能。 在一般情況下的預設行為與它們所提供的外觀會符合您的需求。 如果您需要額外的功能，衍生自這些類別。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [應用程式精靈所建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架視窗樣式](../mfc/frame-window-styles-cpp.md)  
  
-   [變更 MFC 所建立之視窗的樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## <a name="see-also"></a>另請參閱  
 [框架視窗](../mfc/frame-windows.md)

