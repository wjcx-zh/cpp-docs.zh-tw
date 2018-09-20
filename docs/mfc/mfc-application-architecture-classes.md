---
title: MFC 應用程式架構類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32a842d69e227633f8fbd2291a47296d384a75c6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438622"
---
# <a name="mfc-application-architecture-classes"></a>MFC 應用程式架構類別

這個分類中的類別參與架構應用程式的架構。 它們提供常用的功能給大部分的應用程式。 您填入架構以新增應用程式特定的功能。 一般來說，您會藉由從架構類別衍生新類別，然後加入新的成員或覆寫現有的成員函式來進行。

[應用程式精靈](../mfc/reference/mfc-application-wizard.md)產生數種類型的應用程式，全部都以不同方式使用應用程式架構。 SDI (單一文件介面) 和 MDI (多重文件介面) 應用程式會充分利用呼叫文件/檢視架構的部分架構。 其他類型的應用程式 (例如，對話方塊架構的應用程式)、表單架構應用程式和 DLL，僅使用部分的文件/檢視架構功能。

文件/檢視應用程式包含一組或多組文件、檢視和框架視窗。 文件範本物件會與每個文件/檢視/架構集的類別關聯。

雖然您不必在 MFC 應用程式中使用文件/檢視架構，不過還是有一些優點值得如此做。 MFC OLE 容器和伺服器支援是以文件/檢視架構為基礎，如同對於列印和預覽列印的支援。

所有的 MFC 應用程式具有至少兩個物件︰ 應用程式物件衍生自[CWinApp](../mfc/reference/cwinapp-class.md)，以及某種形式的主視窗物件 （通常間接） 衍生自[CWnd](../mfc/reference/cwnd-class.md)。 (大多數情況下，主視窗衍生自[CFrameWnd](../mfc/reference/cframewnd-class.md)， [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，或[CDialog](../mfc/reference/cdialog-class.md)，其中都衍生自`CWnd`。)

使用文件/檢視架構的應用程式包含其他物件。 主體物件如下：

- 應用程式物件衍生自類別[CWinApp](../mfc/reference/cwinapp-class.md)，如先前所述。

- 一或多個文件類別物件衍生自類別[CDocument](../mfc/reference/cdocument-class.md)。 文件類別物件負責內部表示檢視中所操作的資料。 它們可能與資料檔案關聯。

- 一或多個檢視物件衍生自類別[CView](../mfc/reference/cview-class.md)。 每個檢視是附加到文件並與框架視窗關聯的視窗。 檢視顯示和操作文件類別物件中所包含的資料。

文件/檢視應用程式也包含框架視窗 (衍生自[CFrameWnd](../mfc/reference/cframewnd-class.md)) 和文件範本 (衍生自[CDocTemplate](../mfc/reference/cdoctemplate-class.md))。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

