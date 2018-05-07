---
title: 執行緒特定的熱鍵 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdd6cf2f2bb76c30f4cc00d75eb55d7d2c01fa7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="thread-specific-hot-keys"></a>執行緒特定的熱鍵
應用程式設定的執行緒特定的熱鍵 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 使用 Windows **RegisterHotKey**函式。 當使用者按下執行緒特定的熱鍵時，Windows 就會張貼[WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279)訊息至特定的執行緒訊息佇列的開頭。 **WM_HOTKEY**訊息包含虛擬按鍵碼、 移位狀態，以及使用者定義的特定熱鍵已按下的 ID。 如需標準虛擬按鍵碼的清單，請參閱 Winuser.h。 如需有關這個方法的詳細資訊，請參閱[RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
 請注意，移位狀態旗標來呼叫中使用**RegisterHotKey**不是所傳回的相同[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成員函式; 您必須將轉譯，這些旗標才能呼叫**RegisterHotKey**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)

