---
title: Run 成員函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 446b1b6fc2a5265e2c4eb8a608ff8b4f0028c57d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408228"
---
# <a name="run-member-function"></a>Run 成員函式

Framework 應用程式花費最多時間在[執行](../mfc/reference/cwinapp-class.md#run)類別成員函式[CWinApp](../mfc/reference/cwinapp-class.md)。 在初始化之後，`WinMain`呼叫`Run`處理的訊息迴圈。

`Run` 循環訊息迴圈，檢查訊息佇列中可用的訊息。 如果訊息可用，`Run`分派它以進行動作。 如果沒有訊息可供使用，這通常是 0、1、true`Run`呼叫`OnIdle`執行任何閒置時間處理，您或架構可能需要完成。 如果沒有想要的訊息和閒置處理，則應用程式會等候直到有動作發生。 應用程式終止時，`Run`呼叫`ExitInstance`。 中的圖表[OnIdle 成員函式](../mfc/onidle-member-function.md)訊息迴圈中顯示的動作順序。

訊息分派取決於訊息的類型。 如需詳細資訊，請參閱 <<c0> [ 訊息和架構中的命令](../mfc/messages-and-commands-in-the-framework.md)。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
