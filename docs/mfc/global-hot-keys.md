---
title: "全域熱鍵 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82297507d8725e6292def759272f48d0d63e84b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="global-hot-keys"></a>全域熱鍵
全域熱鍵是與特定藉視窗相關聯。 它可讓使用者啟動視窗中，從系統的任何部分。 應用程式設定特定視窗的全域快速鍵傳送[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)至該視窗的訊息。 比方說，如果`m_HotKeyCtrl`是[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)物件和`pMainWnd`是指標，要在按下便捷鍵時要啟動視窗中，您可以使用下列程式碼產生關聯的熱鍵控制項中指定所指向視窗`pMainWnd`。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 每當使用者按下的全域快速鍵，指定視窗收到[WM_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360)指定訊息**SC_HOTKEY**做為命令的類型。 此訊息也會啟動所收到的視窗。 因為這則訊息不包含已按下的確切索引鍵上的所有資訊，使用此方法不允許區別不同的快速鍵可能附加到相同的視窗。 熱鍵會一直傳送的應用程式有效**WM_SETHOTKEY**結束。  
  
## <a name="see-also"></a>請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)

