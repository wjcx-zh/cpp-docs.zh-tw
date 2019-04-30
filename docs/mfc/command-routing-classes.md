---
title: 命令路由類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: 264e931ba0468cdc44f27c55e5d259948c5392b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406050"
---
# <a name="command-routing-classes"></a>命令路由類別

當使用者透過使用滑鼠選擇功能表或控制列按鈕來與應用程式互動時，應用程式會從受影響的使用者介面物件傳送訊息至適當的命令目標物件。 命令目標類別衍生自`CCmdTarget`包括[CWinApp](../mfc/reference/cwinapp-class.md)， [CWnd](../mfc/reference/cwnd-class.md)， [CDocTemplate](../mfc/reference/cdoctemplate-class.md)， [CDocument](../mfc/reference/cdocument-class.md)， [CView](../mfc/reference/cview-class.md)，以及從它們衍生的類別。 架構支援自動的命令路由，以便可以由目前在應用程式中作用中的最適當物件來處理命令。

類別的物件`CCmdUI`傳遞至命令目標的更新命令 UI ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) 處理常式，讓您更新的特定命令的使用者介面的狀態 （例如，若要檢查或移除檢查與功能表項目）。 您呼叫 `CCmdUI` 物件的成員函式來更新 UI 物件的狀態。 這個程序與 UI 物件與特定命令關聯的是功能表項目或按鈕 (或者二者都關聯) 相同。

[CCmdTarget](../mfc/reference/ccmdtarget-class.md)<br/>
做為可以接收和回應訊息之物件的所有類別的基底類別。

[CCmdUI](../mfc/reference/ccmdui-class.md)<br/>
提供程式設計介面，以更新使用者介面物件 (例如功能表項目或控制列按鈕)。 命令目標物件會使用此物件啟用、停用、檢查和/或清除使用者介面物件。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
