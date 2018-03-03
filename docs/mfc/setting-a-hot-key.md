---
title: "設定熱鍵 |Microsoft 文件"
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
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9cd52fca8415196fc1393cc49fe7830f6ca2cfd1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setting-a-hot-key"></a>設定熱鍵
您的應用程式可以使用熱鍵所提供的資訊 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有兩種控制項：  
  
-   設定啟動藉視窗所傳送的全域快速鍵[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)視窗啟動的訊息。  
  
-   藉由呼叫 Windows 函式，設定執行緒特定的熱鍵[RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## <a name="see-also"></a>請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)

