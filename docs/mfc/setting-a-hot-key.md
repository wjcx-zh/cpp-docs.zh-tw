---
title: 設定熱鍵 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3987ddee98ae35e02a181e38cd71f181801aeb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setting-a-hot-key"></a>設定熱鍵
您的應用程式可以使用熱鍵所提供的資訊 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有兩種控制項：  
  
-   設定啟動藉視窗所傳送的全域快速鍵[WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284)視窗啟動的訊息。  
  
-   藉由呼叫 Windows 函式，設定執行緒特定的熱鍵[RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)

