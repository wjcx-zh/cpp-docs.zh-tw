---
title: 建立工具提示的方法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26f6e7cbf8c6464afa90c52f9cd91dcdb55de767
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="methods-of-creating-tool-tips"></a>建立工具提示的方法
MFC 提供三個類別來建立和管理工具提示控制項： [CWnd](../mfc/reference/cwnd-class.md)， [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)， [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)和[CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). 這些類別中的工具提示成員函式包裝 Windows 通用控制項 API。 `CToolBarCtrl` 類別和 `CToolTipCtrl` 類別衍生自 `CWnd` 類別。  
  
 `CWnd` 提供四個成員函式來建立和管理工具提示： [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)， [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips)， [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage)，和[OnToolHitTest](../mfc/reference/cwnd-class.md#ontoolhittest). 請參閱這些個別成員函式以取得如何實作工具提示的詳細資訊。  
  
 如果您建立工具列，使用`CToolBarCtrl`，您可以實作該工具列，使用下列成員函式的工具提示： [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips)和[SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips)。 請參閱這些個別成員函式和[處理工具提示通知](../mfc/handling-tool-tip-notifications.md)如需有關如何實作工具提示。  
  
 `CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 一個工具提示控制項可以提供多個工具的資訊。 工具可以是視窗 (例如子視窗或控制項)，或是視窗工作區中應用程式定義的矩形區域。 [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md)類別衍生自`CToolTipCtrl`，並提供額外的視覺化樣式和功能。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)

