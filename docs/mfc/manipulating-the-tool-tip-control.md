---
title: "管理工具提示控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae30c39a26379aaa8a6f786b5fe2542abde2c2df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="manipulating-the-tool-tip-control"></a>管理工具提示控制項
`CToolTipCtrl` 類別提供一組成員函式，其可以控制 `CToolTipCtrl` 物件和工具提示視窗的各種屬性。  
  
 初始、 快顯和重新顯示期間工具提示視窗可以設定和擷取呼叫[GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime)和[SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime)。  
  
 使用下列函式變更工具提示視窗的外觀：  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin)和[SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin)擷取和設定之間工具提示框線和工具提示文字。  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth)和[SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth)擷取和設定的最大寬度的工具提示視窗。  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor)和[SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor)擷取和設定背景色彩的工具提示視窗。  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor)和[SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor)擷取和設定文字色彩的工具提示視窗。  
  
 為了讓工具提示控制項的重要的訊息，例如通知**WM_LBUTTONXXX**訊息，您必須將訊息轉送至工具提示控制項。 這項轉送的最佳方法是對進行呼叫[Relayevent](../mfc/reference/ctooltipctrl-class.md#relayevent)，請在`PreTranslateMessage`函式的主控視窗。 下列範例說明可能的方法 (假設工具提示控制項名為 `m_ToolTip`)：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 若要立即移除工具提示視窗，呼叫[Pop](../mfc/reference/ctooltipctrl-class.md#pop)成員函式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)

