---
title: "使用 CHotKeyCtrl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CHotKeyCtrl
dev_langs: C++
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36d577369dea4f5fe2fffa9801bbd8ae8501f71a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-chotkeyctrl"></a>使用 CHotKeyCtrl
熱鍵控制項，類別所代表[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)，是一個視窗，顯示使用者輸入此功能，例如 CTRL + SHIFT + Q 的按鍵組合的文字表示。 它也會以虛擬按鍵碼和表示移位狀態的一組旗標的形式，來保持此按鍵的內部表示。 熱鍵控制項不會實際設定熱鍵，是否設定取決於您的程式  (如需標準虛擬按鍵碼的清單，請參閱 Winuser.h.)。  
  
 使用熱鍵控制項，來取得使用者針對要與視窗或執行緒關聯的熱鍵進行的輸入。 熱鍵控制項通常用於對話方塊中，例如當要求使用者指派熱鍵時就可能會顯示。 從熱鍵控制項擷取描述熱鍵的值，以及呼叫適當的函式使熱鍵與視窗或執行緒相關聯，是由您的程式負責。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [使用熱鍵控制項](../mfc/using-a-hot-key-control.md)  
  
-   [設定熱鍵](../mfc/setting-a-hot-key.md)  
  
-   [全域熱鍵](../mfc/global-hot-keys.md)  
  
-   [執行緒特定的熱鍵](../mfc/thread-specific-hot-keys.md)  
  
## <a name="see-also"></a>請參閱  
 [控制項](../mfc/controls-mfc.md)

