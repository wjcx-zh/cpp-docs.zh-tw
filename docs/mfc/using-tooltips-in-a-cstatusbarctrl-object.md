---
title: "在 CStatusBarCtrl 物件中使用工具提示 |Microsoft 文件"
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
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3e2d7f2ee90b7389ad3602e808213c3803dd5ad1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>在 CStatusBarCtrl 物件中使用工具提示
若要啟用狀態列控制項的工具提示，請建立`CStatusBarCtrl`物件**SBT_TOOLTIPS**樣式。  
  
> [!NOTE]
>  如果您是使用 `CStatusBar` 物件實作自己的狀態列，請使用 `CStatusBar::CreateEx` 函式。 它可讓您指定的內嵌其他樣式**CStatusBarCtrl**物件。  
  
 一次`CStatusBarCtrl`成功建立物件，請使用[cstatusbarctrl:: Settiptext](../mfc/reference/cstatusbarctrl-class.md#settiptext)和[cstatusbarctrl:: Gettiptext](../mfc/reference/cstatusbarctrl-class.md#gettiptext)設定和擷取特定窗格的提示文字。  
  
 當工具提示設定時，只有在組件沒有圖示和文字才會顯示，或者無法在組件中顯示所有文字時才顯示。 在簡單模式中不支援工具提示。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

