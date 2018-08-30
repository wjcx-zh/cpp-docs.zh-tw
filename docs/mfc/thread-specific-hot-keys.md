---
title: 執行緒特定的熱鍵 |Microsoft Docs
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
ms.openlocfilehash: f480b293e9c57e7fa189c6427ab39147681cfdaf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206856"
---
# <a name="thread-specific-hot-keys"></a>執行緒特定的熱鍵
應用程式設定執行緒專用的快速鍵 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 利用 Windows`RegisterHotKey`函式。 當使用者按下執行緒特定的熱鍵時，Windows 會張貼[WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey)訊息至特定執行緒之訊息佇列的開頭。 WM_HOTKEY 訊息包含虛擬按鍵碼、 移位狀態和使用者定義的已按下特定快速鍵的識別碼。 如需標準虛擬按鍵碼的清單，請參閱 Winuser.h。 如需有關這個方法的詳細資訊，請參閱 < [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
 請注意，移位狀態旗標來呼叫中使用`RegisterHotKey`不是所傳回的相同[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成員函式; 您必須將轉譯這些旗標，然後再呼叫`RegisterHotKey`。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)

