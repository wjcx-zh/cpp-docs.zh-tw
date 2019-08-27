---
title: 設定熱鍵
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: 7b49f24039b130f74693e7567f5287476126f225
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511215"
---
# <a name="setting-a-hot-key"></a>設定熱鍵

您的應用程式可以透過下列兩種方式的其中一種, 使用快速鍵 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 控制項所提供的資訊:

- 藉由將[WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey)訊息傳送至要啟動的視窗, 設定啟用 nonchild 視窗的全域熱鍵。

- 藉由呼叫 Windows 函數[RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)來設定執行緒特定的熱鍵。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
