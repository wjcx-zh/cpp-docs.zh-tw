---
title: 處理工具提示的 TTN_NEEDTEXT 告知
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 75850dbf92587cf654d4f7a39ea54af1fd9dd5bd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620073"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>處理工具提示的 TTN_NEEDTEXT 告知

[啟用工具提示](enabling-tool-tips.md)時，您可以將下列專案新增至您的擁有者視窗的訊息對應，以處理**TTN_NEEDTEXT**訊息：

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
當此按鈕需要文字時，所要呼叫的成員函式。

請注意，工具提示的識別碼一律為0。

在類別定義中宣告您的處理常式函式，如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

其中的斜體參數如下：

*id*<br/>
傳送通知之控制項的識別碼。 未使用。 控制項識別碼取自**NMHDR**結構。

*pNMHDR*<br/>
[NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow)結構的指標。 此結構也會在[TOOLTIPTEXT 結構](tooltiptext-structure.md)中進一步討論。

*pResult*<br/>
您可以在傳回之前設定的結果程式碼指標。 **TTN_NEEDTEXT**處理常式可以忽略*pResult*參數。

表單檢視通知處理常式的範例如下：

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

呼叫 `EnableToolTips` （此片段取自 `OnInitDialog` ）：

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>另請參閱

[非衍生自 CFrameWnd 之視窗中的工具提示](tool-tips-in-windows-not-derived-from-cframewnd.md)
