---
title: 框架視窗的功能 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], about frame widows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ed903238a812188d73093211265c9c8c028b0ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382563"
---
# <a name="what-frame-windows-do"></a>框架視窗執行什麼功能
除了框架檢閱以外，框架視窗負責協調框架與其檢閱及與應用程式相關的各種工作。 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)和[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)繼承自[CFrameWnd](../mfc/reference/cframewnd-class.md)，因此，它們需要`CFrameWnd`功能，以及它們所加入的新功能。 子視窗的範例包括檢視、控制項 (例如按鈕和清單方塊)，以及控制列 (包括工具列、狀態列和對話方塊列)。  
  
 框架視窗負責管理其子視窗的配置。 在 MFC 架構中，框架視窗可在其工作區內放置所有控制列、檢視和其他子視窗。  
  
 框架視窗也會轉送命令給其檢視，並且可回應來自控制項視窗的通知訊息。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [控制列 （如何調整大小成框架視窗）](../mfc/control-bars.md)  
  
-   [管理功能表、 控制列和快速鍵 （如何調整大小成框架視窗）](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [命令路由 （從框架視窗至其檢視和其他命令目標）](../mfc/command-routing.md)  
  
-   [文件 /View 架構](../mfc/document-view-architecture.md)  
  
-   [控制列](../mfc/control-bars.md)  
  
-   [控制項](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>另請參閱  
 [框架視窗](../mfc/frame-windows.md)

