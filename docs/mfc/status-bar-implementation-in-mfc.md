---
title: 在 MFC 中的狀態列實作 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COldStatusBar
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13a85ba03089a9536c8c6512bccd09f1eb34c0a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="status-bar-implementation-in-mfc"></a>MFC 中的狀態列實作
A [CStatusBar](../mfc/reference/cstatusbar-class.md)物件是一種控制列的資料列文字輸出窗格。 輸出窗格通常用來做為訊息列和狀態指示器。 範例包括簡要說明選取的功能表命令的功能表說明訊息行和顯示 SCROLL LOCK、 NUM LOCK 和其他按鍵的狀態指標。  
  
 根據 MFC 4.0 版，狀態列會使用實作類別[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)，以封裝狀態列通用控制項。 回溯相容性，MFC 會保留舊的狀態 列實作類別中**COldStatusBar**。 舊版的 MFC 的文件描述**COldStatusBar**下`CStatusBar`。  
  
 [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)，成員函式新增到 MFC 4.0 可讓您利用狀態列自訂和其他功能的 Windows 通用控制項的支援。 `CStatusBar` 成員函式可讓您大部分的 Windows 通用控制項; 功能不過，當您呼叫`GetStatusBarCtrl`，您就能給予您狀態列更多狀態列的特性。 當您呼叫`GetStatusBarCtrl`，它會傳回參考`CStatusBarCtrl`物件。 您可以使用該參考來操作狀態列控制項。  
  
 下圖顯示的數個標記的狀態列。  
  
 ![狀態列](../mfc/media/vc37dy1.gif "vc37dy1")  
狀態列  
  
 工具列上，例如狀態列物件內嵌在其父框架視窗，並建構框架視窗時自動建構。 [狀態] 列中的，所有控制列，例如，會自動終結也會在終結父框架時。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [更新狀態列窗格的文字](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   MFC 類別[CStatusBar](../mfc/reference/cstatusbar-class.md)和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [控制列](../mfc/control-bars.md)  
  
-   [對話方塊列](../mfc/dialog-bars.md)  
  
-   [工具列 （MFC 工具列實作）](../mfc/mfc-toolbar-implementation.md)  
  
## <a name="see-also"></a>另請參閱  
 [狀態列](../mfc/status-bars.md)

