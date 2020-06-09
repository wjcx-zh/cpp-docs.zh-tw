---
title: MFC 應用程式架構類別
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 455a49a4f93f2fb2590447071edca76a32cbc5dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618028"
---
# <a name="mfc-application-architecture-classes"></a>MFC 應用程式架構類別

這個分類中的類別參與架構應用程式的架構。 它們提供常用的功能給大部分的應用程式。 您填入架構以新增應用程式特定的功能。 一般來說，您會藉由從架構類別衍生新類別，然後加入新的成員或覆寫現有的成員函式來進行。

[應用程式的嚮導](reference/mfc-application-wizard.md)會產生數種類型的應用程式，而它們全都以不同的方式使用應用程式架構。 SDI (單一文件介面) 和 MDI (多重文件介面) 應用程式會充分利用呼叫文件/檢視架構的部分架構。 其他類型的應用程式 (例如，對話方塊架構的應用程式)、表單架構應用程式和 DLL，僅使用部分的文件/檢視架構功能。

文件/檢視應用程式包含一組或多組文件、檢視和框架視窗。 文件範本物件會與每個文件/檢視/架構集的類別關聯。

雖然您不必在 MFC 應用程式中使用文件/檢視架構，不過還是有一些優點值得如此做。 MFC OLE 容器和伺服器支援是以文件/檢視架構為基礎，如同對於列印和預覽列印的支援。

所有 MFC 應用程式都有至少兩個物件：衍生自[CWinApp](reference/cwinapp-class.md)的應用程式物件，以及某種類型的主視窗物件（通常間接），衍生自[CWnd](reference/cwnd-class.md)。 （最常見的情況是，主視窗衍生自[CFrameWnd](reference/cframewnd-class.md)、 [CMDIFrameWnd](reference/cmdiframewnd-class.md)或[CDialog](reference/cdialog-class.md)，這些都是衍生自 `CWnd` ）。

使用文件/檢視架構的應用程式包含其他物件。 主體物件如下：

- 如先前所述，從類別[CWinApp](reference/cwinapp-class.md)衍生的應用程式物件。

- 衍生自類別[CDocument](reference/cdocument-class.md)的一或多個檔類別物件。 文件類別物件負責內部表示檢視中所操作的資料。 它們可能與資料檔案關聯。

- 衍生自類別[CView](reference/cview-class.md)的一個或多個 view 物件。 每個檢視是附加到文件並與框架視窗關聯的視窗。 檢視顯示和操作文件類別物件中所包含的資料。

檔/視圖應用程式也包含框架視窗（衍生自[CFrameWnd](reference/cframewnd-class.md)）和檔範本（衍生自[CDocTemplate](reference/cdoctemplate-class.md)）。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
