---
title: Run 成員函式
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8271a10ad7439d2795dcc45d667b23b0932a0486
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271823"
---
# <a name="run-member-function"></a>Run 成員函式

Framework 應用程式花費最多時間在[執行](../mfc/reference/cwinapp-class.md#run)類別成員函式[CWinApp](../mfc/reference/cwinapp-class.md)。 在初始化之後，`WinMain`呼叫`Run`處理的訊息迴圈。

`Run` 循環訊息迴圈，檢查訊息佇列中可用的訊息。 如果訊息可用，`Run`分派它以進行動作。 如果沒有訊息可供使用，這通常是 0、1、true`Run`呼叫`OnIdle`執行任何閒置時間處理，您或架構可能需要完成。 如果沒有想要的訊息和閒置處理，則應用程式會等候直到有動作發生。 應用程式終止時，`Run`呼叫`ExitInstance`。 中的圖表[OnIdle 成員函式](../mfc/onidle-member-function.md)訊息迴圈中顯示的動作順序。

訊息分派取決於訊息的類型。 如需詳細資訊，請參閱 <<c0> [ 訊息和架構中的命令](../mfc/messages-and-commands-in-the-framework.md)。

## <a name="see-also"></a>另請參閱

[CWinApp:應用程式類別](../mfc/cwinapp-the-application-class.md)
