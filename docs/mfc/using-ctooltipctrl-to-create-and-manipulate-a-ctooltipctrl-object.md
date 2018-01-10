---
title: "使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CToolTipCtrl
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da4c98e327d2d78050410e75869c894d73324281
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>使用 CToolTipCtrl 建立及管理 CToolTipCtrl 物件
以下是範例[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)使用量：  
  
### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>建立和操作 CToolTipCtrl  
  
1.  建構 `CToolTipCtrl` 物件。  
  
2.  呼叫[建立](../mfc/reference/ctooltipctrl-class.md#create)建立 Windows 工具提示通用控制項並將其附加至`CToolTipCtrl`物件。  
  
3.  呼叫[AddTool](../mfc/reference/ctooltipctrl-class.md#addtool)要與工具提示控制項註冊工具，使游標位於工具上時，會顯示工具提示中所儲存的資訊。  
  
4.  呼叫[SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo)來設定工具提示會維護工具的資訊。  
  
5.  呼叫[SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect)設定工具的新週框矩形。  
  
6.  呼叫[HitTest](../mfc/reference/ctooltipctrl-class.md#hittest)以測試點，以判斷它是否在指定之工具的週框矩形內，如果是這樣，則擷取工具的相關資訊。  
  
7.  呼叫[GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount)以擷取工具計數註冊工具提示控制項。  
  
## <a name="see-also"></a>請參閱  
 [使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [控制項](../mfc/controls-mfc.md)

