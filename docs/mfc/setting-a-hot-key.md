---
title: 設定熱鍵 |Microsoft Docs
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
ms.openlocfilehash: 254d7532b83a4f30c0029b2488bb0b2111cce31d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219393"
---
# <a name="setting-a-hot-key"></a>設定熱鍵
您的應用程式可以使用熱鍵所提供的資訊 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有兩種控制項：  
  
-   設定用來啟用藉視窗所傳送的全域快速鍵[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)視窗啟動的訊息。  
  
-   設定藉由呼叫 Windows 函式的執行緒特定的熱鍵[RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)

