---
title: 設定熱鍵
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a77aad4881acd04c6dabb6dce90acc01be2cfbc8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307779"
---
# <a name="setting-a-hot-key"></a>設定熱鍵

您的應用程式可以使用熱鍵所提供的資訊 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有兩種控制項：

- 設定用來啟用藉視窗所傳送的全域快速鍵[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)視窗啟動的訊息。

- 設定藉由呼叫 Windows 函式的執行緒特定的熱鍵[RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
