---
title: 使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb378bba1505f8bbc3739c070d52abe9ef4f8afc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953821"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>使用 CStatusBarCtrl 建立 CStatusBarCtrl 物件
以下是範例的典型用法[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>使用組件中的狀態列控制項  
  
1.  建構 `CStatusBarCtrl` 物件。  
  
2.  呼叫[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)如果您想要設定狀態列控制項的最小高度的繪圖區域。  
  
3.  呼叫[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)設定狀態列控制項的背景色彩。  
  
4.  呼叫[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)在狀態列控制項與每個部分的右邊緣的座標中設定之部分的數目。  
  
5.  呼叫[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)設定狀態列控制項的指定組件中的文字。 訊息已變更，使其在控制項接著接收 WM_PAINT 訊息時，顯示新的文字控制項部分失效。  
  
 在某些情況下，[狀態] 列只需要顯示一行文字。 在此情況下，呼叫以[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)。 如此會將狀態列控制項放入 「 簡單 」 模式中，會顯示單行文字。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

