---
title: "使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94043fa3ff8dbbc68c91b8d621303ab4afe29877
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件
以下是範例的典型用法[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>使用組件中的狀態列控制項  
  
1.  建構 `CStatusBarCtrl` 物件。  
  
2.  呼叫[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)如果您想要設定狀態列控制項的最小高度的繪圖區域。  
  
3.  呼叫[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)設定狀態列控制項的背景色彩。  
  
4.  呼叫[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)在狀態列控制項與每個部分的右邊緣的座標中設定之部分的數目。  
  
5.  呼叫[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)設定狀態列控制項的指定組件中的文字。 此訊息會使已變更的控制項部分失效，使其在控制項接著接收 `WM_PAINT` 訊息時顯示新的文字。  
  
 在某些情況下，[狀態] 列只需要顯示一行文字。 在此情況下，呼叫以[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)。 如此會將狀態列控制項放入 「 簡單 」 模式中，會顯示單行文字。  
  
## <a name="see-also"></a>請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

