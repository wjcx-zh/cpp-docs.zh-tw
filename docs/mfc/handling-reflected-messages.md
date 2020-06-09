---
title: 處理反映訊息
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 8907b432cf4dabad33c0925b841f65dfc57c6295
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620145"
---
# <a name="handling-reflected-messages"></a>處理反映訊息

訊息反映可讓您處理控制項的訊息，例如控制項本身內的**WM_CTLCOLOR**、 **WM_COMMAND**和**WM_NOTIFY**。 這可讓控制項更具獨立 (Self-Contained) 性及可移植性。 搭配 Windows 通用控制項以及 ActiveX 控制項 (先前稱為 OLE 控制項) 使用的機制。

訊息反映可讓您更容易地重複使用 `CWnd` 衍生類別。 訊息反映會透過[CWnd：： OnChildNotify](reference/cwnd-class.md#onchildnotify)，使用特殊的**ON_XXX_REFLECT**訊息對應專案來運作：例如， **ON_CTLCOLOR_REFLECT**和**ON_CONTROL_REFLECT**。 [技術提示 62](tn062-message-reflection-for-windows-controls.md)會更詳細地說明訊息反映。

## <a name="what-do-you-want-to-do"></a>您想要做什麼

- [進一步了解訊息反映](tn062-message-reflection-for-windows-controls.md)

- [實作通用控制項的訊息反映](tn062-message-reflection-for-windows-controls.md)

- [實作 ActiveX 控制項的訊息反映](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](declaring-message-handler-functions.md)
