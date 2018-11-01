---
title: 處理反映訊息
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 9b580c0c8b8fc970d69f5c57f69bbbbe65e22497
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449864"
---
# <a name="handling-reflected-messages"></a>處理反映訊息

訊息反映可讓您處理訊息的控制項，例如**WM_CTLCOLOR**， **WM_COMMAND**，並**WM_NOTIFY**，控制項本身。 這可讓控制項更具獨立 (Self-Contained) 性及可移植性。 搭配 Windows 通用控制項以及 ActiveX 控制項 (先前稱為 OLE 控制項) 使用的機制。

訊息反映可讓您更容易地重複使用 `CWnd` 衍生類別。 訊息透過反映 works [On_xxx_reflect](../mfc/reference/cwnd-class.md#onchildnotify)，使用特殊**ONCHILDNOTIFY**訊息對應項目： 例如， **ON_CTLCOLOR_REFLECT**和**ON_CONTROL_REFLECT**。 [技術提示 62](../mfc/tn062-message-reflection-for-windows-controls.md)說明詳細的訊息反映。

## <a name="what-do-you-want-to-do"></a>您要做什麼

- [深入了解訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)

- [實作通用控制項的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)

- [實作 ActiveX 控制項的訊息反映](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)
