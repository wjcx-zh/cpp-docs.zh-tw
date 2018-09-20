---
title: 處理反映訊息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99fc9c30ea85ba3f94fa811464f023da0eeea37e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438674"
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
