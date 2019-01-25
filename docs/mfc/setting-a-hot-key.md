---
title: 設定熱鍵
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: ebaddb4a64a4d9d47b82fd36f118c74527554e53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893220"
---
# <a name="setting-a-hot-key"></a>設定熱鍵

您的應用程式可以使用熱鍵所提供的資訊 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 中有兩種控制項：

- 設定用來啟用藉視窗所傳送的全域快速鍵[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)視窗啟動的訊息。

- 設定藉由呼叫 Windows 函式的執行緒特定的熱鍵[RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey)。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

