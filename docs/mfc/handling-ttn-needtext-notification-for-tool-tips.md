---
title: 處理工具提示的 TTN_NEEDTEXT 告知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e3b54ebc4c624b3be098f2bbf3ec30c6b70a38c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372427"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>處理工具提示的 TTN_NEEDTEXT 告知

做為一部分[啟用工具提示](../mfc/enabling-tool-tips.md)，您處理**TTN_NEEDTEXT**藉由將下列項目加入至主控視窗的訊息對應的訊息：

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
此按鈕需要文字時要呼叫此成員函式。

請注意，工具提示的識別碼一律為 0。

宣告您的處理常式函式，在類別定義如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

其中的斜體的參數如下：

*id*<br/>
傳送通知之控制項的識別項。 未使用。 控制項 id 取自**NMHDR**結構。

*pNMHDR*<br/>
指標[NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa)結構。 也會討論這個結構中進一步[TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)。

*pResult*<br/>
您設定的指標，結果程式碼前您傳回。 **TTN_NEEDTEXT**處理常式可以忽略*pResult*參數。

表單檢視的通知處理常式的範例：

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

呼叫`EnableToolTips`(取自此片段`OnInitDialog`):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>另請參閱

[非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

