---
title: 非命令訊息如何連接其處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: c7b2bf819c5305da4039fae172578298d3b4e609
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618500"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令訊息如何連接其處理常式

不同于命令，標準 Windows 訊息不會透過一連串的命令目標來路由傳送，而是由 Windows 傳送訊息的視窗處理。 視窗可能是主框架視窗、MDI 子視窗、標準控制項、對話方塊、視圖，或其他類型的子視窗。

在執行時間，每個 Windows 視窗都會附加至 `CWnd` 具有本身相關聯訊息對應和處理常式函式的視窗物件（直接或間接衍生自）。 架構會使用訊息對應（如命令），將傳入訊息對應至處理常式。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)
