---
title: 啟用工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: bdd5c54f9174c42e17db0be7e13ea31acfea2dcf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615721"
---
# <a name="enabling-tool-tips"></a>啟用工具提示

您可以讓工具提示支援視窗的子控制項 (例如在表單檢視或對話方塊的控制項)。

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>為視窗的子控制項啟用工具提示

1. 對於您想提供工具提示的視窗，呼叫視窗的 `EnableToolTips`。

1. 為[TTN_NEEDTEXT 通知](handling-ttn-needtext-notification-for-tool-tips.md)處理常式中的每個控制項提供字串。 處理常式是在包含子控制項視窗的訊息對應中 (例如，您的表單檢視類別)。 這個處理常式應該呼叫可識別控制項的函式，並設定**pszText**來指定工具提示控制項所使用的文字。

## <a name="see-also"></a>另請參閱

[非衍生自 CFrameWnd 之視窗中的工具提示](tool-tips-in-windows-not-derived-from-cframewnd.md)
